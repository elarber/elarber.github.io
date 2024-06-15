---
title: 使用electron+vue技术快速开发桌面端应用

index_img: https://img-blog.csdnimg.cn/2a9a35a2ae4a48da9af512dfa41ecf4d.png
lazyload: true
categories:
- electron
tags:
- electron
- 终端



---










![](https://img-blog.csdnimg.cn/2a9a35a2ae4a48da9af512dfa41ecf4d.png)


# 版本支持
```
node      v16.15.1
npm       8.11.0
```


# 官方文档
- [vue2](https://v2.cn.vuejs.org/)
- [electronjs](https://www.electronjs.org/zh/)


# 构建应用
1. vue create demo
2. cd demo
3. vue add electron-builder
  此处会提示选择electron版本，选最新的即可

结束后看package.json
![](https://img-blog.csdnimg.cn/a5a7bad458d64b3097ca21be8028dc3b.png)

# 启动应用
```
npm run electron:serve
```


# 启动效果
![](https://img-blog.csdnimg.cn/53eab1fa9a674b4fabc305d5b0c4e259.png)


# 目录结构
![](https://img-blog.csdnimg.cn/53db442e4f554e22a7efdf2cf9863ddf.png)

# 业务代码区域
![](https://img-blog.csdnimg.cn/f5d14bc563904b099eb9fa30a64611ac.png)




![](https://img-blog.csdnimg.cn/62e53eb7bf3646f6a69954b92d2d752b.png)



