---
title: hexo接入github Discussions评论系统
index_img: https://img-blog.csdnimg.cn/direct/2bf1331ec09e46b6a0f64f12542ebf1c.png
lazyload: true
categories:
- hexo
tags:
- hexo
- hexo主题
- 博客系统
- 评论系统
- 



---













![](https://img-blog.csdnimg.cn/direct/2bf1331ec09e46b6a0f64f12542ebf1c.png)


# 评论存储仓
可以是你的博客项目的(github)仓库，也可以单独新建一个评论存储仓库。
我的博客项目在gitee上，就以新建存储仓为例：
![](https://img-blog.csdnimg.cn/direct/a2ce931c28904f88abea6c07db4748cc.png)

使用Discussions评论系统**必须开通Discussions**模块！
![](https://img-blog.csdnimg.cn/direct/febf115919ae4318893ec10c4c985e3f.png)


# 安装giscus插件
[https://github.com/apps/giscus](https://github.com/apps/giscus)
![](https://img-blog.csdnimg.cn/direct/c83f23757f3d4510b671e864bdd7d016.png)

![](https://img-blog.csdnimg.cn/direct/d750cceb5e204ba4a91ab8839715ace3.png)
然后关闭你的安装页面即可



# 生成giscus配置代码
在[https://giscus.app/zh-CN](https://giscus.app/zh-CN)

![](https://img-blog.csdnimg.cn/direct/88175a2d805b40f8969c73c8ecdabe29.png)

![](https://img-blog.csdnimg.cn/direct/164528425412466b84f76567a117277a.png)



# 配置hexo
在你的主题配置文件里配置，我是[fluid](https://fluid-dev.github.io/hexo-fluid-docs/guide/#%E8%AF%84%E8%AE%BA)主题：
![](https://img-blog.csdnimg.cn/direct/56fd12b4542240b5988238e96bd1776f.png)


# 使用评论组件
- ## 放局部：
在哪页面用，就在放哪，比如我在【关于】页用：
![](https://img-blog.csdnimg.cn/direct/52adf2188a41485cb9b0b27c04ac254a.png)



- ## 全局放：
在主题配置文件里，我是[fluid](https://fluid-dev.github.io/hexo-fluid-docs/guide/#%E8%87%AA%E5%AE%9A%E4%B9%89-js-css-html)主题：

![](https://img-blog.csdnimg.cn/direct/1f98e9c36285411a9bd5b9053fe36ccd.png)


# 大功告成
启动项目看看
![](https://img-blog.csdnimg.cn/direct/bdcebd7e8684483783f2718b58659d91.png)

![](https://img-blog.csdnimg.cn/direct/435594028f584d1bb2b770cabe02a442.png)


![](https://img-blog.csdnimg.cn/direct/acf8755c681a4759b2b9266bd684f8bf.png)








