---
title: hexo 修改默认主题

index_img: https://img-blog.csdnimg.cn/direct/88e73bd0ee024acb95fb71c957d72632.gif
lazyload: true
categories:
- hexo
tags:
- hexo
- hexo主题
- 博客系统



---













# 1.选主题
[https://hexo.io/themes/](https://hexo.io/themes/) 比如 [fluid](https://github.com/fluid-dev/hexo-theme-fluid)
```
npm install hexo-theme-fluid
```
![](https://img-blog.csdnimg.cn/direct/3fff91c407b041c184b4ab7e91639a1c.gif)

# 2.修改配置文件
_config.yml  =>  theme
![](https://img-blog.csdnimg.cn/direct/2c73ca16c1c34b0a8a8c0061fbbed5b5.gif)



# 3.创建主题文件
复制一份主题文件 => 改名
![](https://img-blog.csdnimg.cn/direct/955c1b651a604627b9e6f2688366f00d.gif)


# 4.执行新主题
清除缓存
```
hexo clean
```

生成静态文件
```
hexo generate
```

启动项目
```
hexo server
```

看：
![](https://img-blog.csdnimg.cn/direct/88e73bd0ee024acb95fb71c957d72632.gif)


# 效果
![](https://img-blog.csdnimg.cn/direct/fa192ba9b47740a88e99018df79de642.gif)

