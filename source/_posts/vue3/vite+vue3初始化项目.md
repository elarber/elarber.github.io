---
title: vite+vue3初始化项目

index_img: https://img-blog.csdnimg.cn/3954662383314eaa856cfb47947879c9.png
lazyload: true
categories:
- vue3
tags:
- vue3



---











# node环境
> [14.18+，16+](https://cn.vitejs.dev/guide/#scaffolding-your-first-vite-project)。最好是16+


# 初始化项目
执行 ` npm create vue@latest ` 就是基于vite构建的命令了
- 如果是第一次执行会询问安装vite：
![](https://img-blog.csdnimg.cn/e91b10bfb2a04f89bfb90cc2255115c0.png)


- 其他情况会出现：
![](https://img-blog.csdnimg.cn/cf47092a84224a079a20029cdc03c73b.png)




所有选择：

![](https://img-blog.csdnimg.cn/2333c3303c3040c6af64393dc30e09bb.png)



# 目录结构介绍
基本和vue2一个意思
![](https://img-blog.csdnimg.cn/c84b7e1933c74f0e85ec09d910aaaee8.png)

[vite.config.js](https://cn.vitejs.dev/config/shared-options.html)文件如同vue2中的vue.config.js文件，用于配置项目的



# 安装依赖
```
npm install
```
![请添加图片描述](https://img-blog.csdnimg.cn/34fa696f3b614260888e2c8ec89ea989.gif)
![](https://img-blog.csdnimg.cn/658a09975ba3475b84d30061fa093f39.png)


# 启动项目
```
npm run dev
```
![请添加图片描述](https://img-blog.csdnimg.cn/b9b0cb742f0c4f668f74882c0b320411.gif)


结果：

![](https://img-blog.csdnimg.cn/3954662383314eaa856cfb47947879c9.png)


