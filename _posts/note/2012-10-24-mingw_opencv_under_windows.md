---
layout: post
title: windows下使用 MinGW+OpenCV
category: c
tags: [opencv, cmake, mingw]
---

唔大概也只有某星这会干这种蛋疼事了= =.

虽然现在的OpenCV自带了build文件, 不过和本机MinGW版本不合的话会发生很多奇怪的问题, 还是重新编译好了. 装好CMake设好环境变量PATH和OPENCV后: 

```{% highlight sh %}
mkdir ${OPENCV}/build/mingw
cd ${OPENCV}/build/mingw
cmake -G"MSYS Makefiles" ../.. 
make
{% endhighlight %}
```

然后使用下面的CMakeLists建立工程即可, 同样记得在cmake时加上标志 `-G"MSYS Makefiles"` .
<script src="https://gist.github.com/4186692.js?file=CMakeLists.txt"></script>

-----

PS. 编译opencv的vc11版本
require: 安装了vs2012

1. 安装cmake http://www.cmake.org/
2. 将cmake.exe所在路径(比如D:\programming\cmake\bin)加入系统环境变量PATH
3. [开始]-vs提供的命令提示行工具, 

```
cd 你的opencv安装路径/build
mkdir vc11
cd vc11
cmake -G"NMake Makefiles" ../..
nmake
```

4. 完成. 之后参考网络上其他乱七八糟的教程, 所有需要.dll .lib的路径都改到opencv/build/vc11
