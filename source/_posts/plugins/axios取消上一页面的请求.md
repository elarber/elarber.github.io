---
title: axios取消上一页面的请求

index_img: https://img-blog.csdnimg.cn/204a7623d9f140fb9e39c7e8fe0b2df3.png
lazyload: true
categories:
- 前端插件使用
tags:
- axios



---











# 请求拦截
1. 声明变量用于存放请求
2. 请求拦截存放请求
3. 导出请求
![](https://img-blog.csdnimg.cn/204a7623d9f140fb9e39c7e8fe0b2df3.png)



# 导航守卫
1. 导入请求集合
2. 路由前置守卫中遍历取消所有请求
![](https://img-blog.csdnimg.cn/8598dd0e5056442cbbe1bf19033d8549.png)


# 登录失效取消后续请求
![](https://img-blog.csdnimg.cn/a07f18d8f0df4a9b90ff348414ced610.png)





