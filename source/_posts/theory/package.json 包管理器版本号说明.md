---
title: package.json 包管理器版本号说明

index_img: https://img-blog.csdnimg.cn/f127ab4bd62d45fd9a63d9998aa07c56.png
lazyload: true
categories:
- 理论打底
tags:
- package.json



---











![](https://img-blog.csdnimg.cn/f127ab4bd62d45fd9a63d9998aa07c56.png)


- 2.6.14指定版本：比如"vue": "2.6.14"，表示安装2.6.14的版本;

- `~`开头版本：比如 "vue": "~2.6.14"，表示安装2.6.x的最新版本（不低于2.6.5）， 但是不安装2.7.x，也就是说安装时不改变大版本号和次要版本号；

- `^`开头版本：比如 "vue": "^2.6.14"，表示安装2.6.14及以上的版本，但是不安装3.0.0， 也就是说安装时不改变大版本号。

