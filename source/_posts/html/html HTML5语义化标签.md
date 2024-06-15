---
title: html HTML5语义化标签

index_img: https://img-blog.csdnimg.cn/20191017125253955.png
lazyload: true
categories:
- html
tags:
- html
- 语义化


---












- **nav**：导航栏，与ul li a配合使用

- **aside**：主内容无关，一般用于侧边栏

- **main**：主内容区，只一次，此文档中的特有内容，导航、版权、广告不算

- **header**：可多次，可以放在article、section里面

- **footer**：可多次

- **article**：独立内容，比如论坛帖子，博客条目，用户评论等

- **section**：文档中的节，比如章节

- **adress**：地址

![](https://img-blog.csdnimg.cn/20191017125253955.png)

![](https://img-blog.csdnimg.cn/20191017125157423.png)

![](https://img-blog.csdnimg.cn/20191017125334250.png)

![](https://img-blog.csdnimg.cn/20191017124741410.png)
语义化优点：

   1.  易于用户阅读，样式丢失的时候能让页面呈现清晰的结构。
   2. 有利于SEO，搜索引擎根据标签来确定上下文和各个关键字的权重。
   3. 方便其他设备解析，如盲人阅读器根据语义渲染网页
   4. 有利于开发和维护，语义化更具可读性，代码更好维护，与CSS3关系更和谐。


---

1、header

   header定义文档或者文档的部分区域的页眉，应作为介绍内容或者导航链接栏的容器。

   在一个文档中，您可以定义多个header元素，但需要注意的是header元素不能作为address、footer或 header 元素的子元素。

  2、nav

   nav描述一个含有多个超链接的区域，该区域包含跳转到其他页面或页面内部其他部分的链接列表。在一个文档中，可定义多个nav元素。

   3、main

   main>定义文档的主要内容，该内容在文档中应当是独一无二的，不包含任何在文档中重复的内容，比如侧边栏，导航栏链接，版权信息，网站logo，搜索框（除非搜索框作为文档的主要功能）。

   需要注意的是在一个文档中不能出现多个main标签。

   4、article

   article元素表示文档、页面、应用或网站中的独立结构，是可独立分配的、可复用的结构，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。

   当article元素嵌套使用时，则该元素代表与外层元素有关的文章。例如，代表博客评论的article元素可嵌套在代表博客文章的article元素中。

   5、aside

   aside 元素表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分且可以被单独的拆分出来而不会影响整体。通常表现为侧边栏或嵌入内容。

   6、footer

   footer定义最近一个章节内容或者根节点元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。

   使用footer插入联系信息时，应在 footer 元素内使用 address>元素。

   注意不能包含footer或者header

   7、section 表示文档中的一个区域（或节），比如，内容中的一个专题组。

   如果元素内容可以分为几个部分的话，应该使用 article 而不是 section。
不要把 section元素作为一个普通的容器来使用，特别是当section仅仅是为了美化样式或方便脚本使用的时候，应使用div。

   这几个标签，比较容易混淆的是section、article，所以这里特别说明：

Authors are encouraged to use the article element instead of the section element when it would make sense to syndicate the contents of the elemen
如果有必要将元素的内容联合起来，则鼓励作者使用article元素而不是section元素。

   通俗来说就是 article 比 section 更具有独立性、完整性。可通过该段内容脱离了所在的语境，是否完整、独立来判断。

