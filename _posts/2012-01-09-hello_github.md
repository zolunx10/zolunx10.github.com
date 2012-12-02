---
layout: post
title: github:pages使用日记
category: git
tags: [github, blog]
---

> 在wordpress\node.js\heroku\co.de\等等乱七八糟的东西上自己纠结了半天, 总之代码相关的还是直接扔到github上吧囧~

谨在此记录下一个没装jekyll\手写md的家伙的github:pages之旅囧.

## install
按照[官方说明](http://pages.github.com/)建一个 *用户名.github.com* 的repo, 直接扔文件即可, 反正都是静态的= =

第一次push会等十几分钟才刷出页面, 以后收到notification就可以看结果了. 

然后为了搞模板看了半天[jekyll的wiki](https://github.com/mojombo/jekyll/wiki/), 结论:  
别管那么多了, 需要什么直接抄 <https://github.com/mojombo/mojombo.github.com> 就好... 如果你和我一样懒得装ruby, 只需注意下**每个页面头部的[YAML Front Matter](https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter)**.


## layout
建一个 _layout/ , 写html, 完(喂= =. 还有就是每个对应的页面顶端加上Matter

```
layout: [layout filename]
```

模板允许嵌套, 至于具体的内容读取之类参考mojombo的 index和_layout中liquid代码部分. 


## post
_posts/ 下满足

1. 文件名是 YEAR-MONTH-DAY-title.MARKUP 形式

2. 后缀[markup]是 .html .md .markdown .textitle 之一(不确定是否还有其他)

的文件会被读入 site.posts , 且子目录中的会自动成为相应category下的文章[[1]](#post_category). 文件名及url分割参见 <https://github.com/mojombo/jekyll/wiki/permalinks> .


## fallback

- <span name="post_category">如何在url使用category</span>  
可以直接使用文件夹[这里的post.categories部分](ttps://github.com/mojombo/jekyll/wiki/Template-Data), 或者在页面头Matter中用 category 指定.
- 文件头的 Matter **必须**是用**3**个 - 括起. 
- 如果有Markdown错误, 将直接不会build而没有错误提示(比如在'''的块里面写#)
- 分页<https://github.com/mojombo/jekyll/wiki/Pagination>

## TODO

- 我仍未知道在post里显示jekyll代码的话({ %)的话要怎么写OTL
- 搜索
- tag
- 模板优化和SEO(你确定这东西有必要么OTL)


## reference

- 一种"搜索"的实现 <http://developmentseed.org/blog/2011/09/09/jekyll-github-pages/>
- By formatting your blog posts in either Markdown, Textile or HTML, you could use [Liquid](http://www.liquidmarkup.org/) to format your pages.
- markdown css: 直接自剥取github的 .mardown-body 
- 可用变量 <https://github.com/mojombo/jekyll/wiki/Template-Data>
- Liquid for Designers <https://github.com/Shopify/liquid/wiki/Liquid-for-Designers>

-------

## 顺便关于co.de

### 若要重新设定一个域名
只能先删除(然后会被 lock 2 weeks), 请耐心等待╮(╯▽╰)╭

### 其所谓的forward(域名跳转)
其实只是嵌一个iframe到你自己的空间, 而且会带上很醒目的whois广告框... 还不如直接申请网络空间自己做一个= =