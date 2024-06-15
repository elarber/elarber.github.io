---
title: unocss+iconify技术在vue项目中使用20000+的图标

index_img: https://img-blog.csdnimg.cn/direct/2f1d174fcf334192ba92146bc3502288.png
lazyload: true
categories:
- 前端插件使用
tags:
- unocss
- iconify



---













# 安装依赖
```
npm i unocss @iconify/json
```

# 配置依赖
## vue.config.js文件
![](https://img-blog.csdnimg.cn/direct/2f1d174fcf334192ba92146bc3502288.png)






## uno.config.js文件
![](https://img-blog.csdnimg.cn/direct/8a2d8348f9144eaabcd446f61e02aefc.png)



## main.js文件
![](https://img-blog.csdnimg.cn/direct/4284449603cd45fc803bb2551875239b.png)




# 使用图标

```html
<i class="i-fa:user"></i>
<i class="i-fa:key"></i>
```
使用公式 `i-库名:图标名`，class名是 `i-` 开头，跟`库名:图标名`，那都有什么库？什么图标？在[https://icones.js.org/](https://icones.js.org/)

![](https://img-blog.csdnimg.cn/direct/8e301f4debcd4fc7b5d948dc88bf3c39.png)


找几个看看

![](https://img-blog.csdnimg.cn/direct/8f2d9e40b71e4348b5e61e69108304cb.png)


![](https://img-blog.csdnimg.cn/direct/bcbf4da98a8f46f18f47d74d323e840d.png)


**记得加 `i-` 哦**，`i-库名:图标名`
# 效果
看，是异步加载svg的图标
![](https://img-blog.csdnimg.cn/direct/ef2d570d6fd0492fab968630de8d7447.png)




# 动态渲染的问题
动态渲染的标签出不来图标，比如动态渲染的权限菜单栏、或者js创建的标签出不来，不过也有解决办法，就2步

## 下载到本地

建议下载图标比较多的、全面的图库，因为这样使用选择的范围就广泛，比如[arcticons](https://icones.js.org/collection/arcticons)、[Phosphor](https://icones.js.org/collection/ph) 、[Pictogrammers](https://icones.js.org/collection/mdi)、[solar](https://icones.js.org/collection/solar)等

![](https://img-blog.csdnimg.cn/direct/339f8b0eee234ef2ad89ca1e98e4c260.png)

![](https://img-blog.csdnimg.cn/direct/55173cd39b7f4c82a5677b32961cf416.png)


自己处理成 ` ["i-库名:图标名", "i-库名:图标名", "i-库名:图标名"] ` 这种格式的 json

![](https://img-blog.csdnimg.cn/direct/52ba8b98dcd54e5a851ad0e323d4a847.png)


## 配置uno safelist
我以FontAwesome4为例：

![](https://img-blog.csdnimg.cn/direct/621bc551a4df4381aad6b02a0cb08688.png)


出来了
![](https://img-blog.csdnimg.cn/direct/fefe85e756c04bb08fd592230ad00a25.png)
