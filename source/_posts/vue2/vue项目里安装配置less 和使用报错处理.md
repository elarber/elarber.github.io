---
title: vue项目里安装配置less 和使用报错处理

index_img: https://img-blog.csdnimg.cn/20200606104159360.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---











1. 在项目目录下执行安装命令：
```
npm install less less-loader --save-dev
```
如图：
![vue项目里安装配置less【使用报错处理】](https://img-blog.csdnimg.cn/20200606104159360.png)

在`.vue`文件的`style`标签上就能用`lang="less"`了
![](https://img-blog.csdnimg.cn/20210326162246780.png)
但是如果要是使用单独的.less文件，需要在`build/webpack.base.conf.js`文件里配置：

```
{
    test: /\.less$/,
    loader: "style-loader!css-loader!less-loader"
}
```
如图：
![vue项目里安装配置less【使用报错处理】](https://img-blog.csdnimg.cn/20200606104655279.png)

---
---
---
---
---


如果有报错：
在`package.json`文件里把less版本调一下

```json
"less": "^3.9",
"less-loader": "^5.0.0",
```

如图：
![vue项目里安装配置less【使用报错处理】](https://img-blog.csdnimg.cn/2020060614315235.png)

再执给项目行次`npm install`，然后==重启==项目
