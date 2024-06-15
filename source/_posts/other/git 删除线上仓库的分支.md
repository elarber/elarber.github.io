---
title: git 删除线上仓库的分支

index_img: https://img-blog.csdnimg.cn/20200927152627321.png
lazyload: true
categories:
- 前端周边
tags:
- git



---













```
 git push origin --delete 分支
```

比如删除`patch-1`分支：
![](https://img-blog.csdnimg.cn/20200927152627321.png#pic_center)


![](https://img-blog.csdnimg.cn/8b56a908a4b94a20acd4bf34834f7a1f.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)





完事刷新再看：
![](https://img-blog.csdnimg.cn/20200927152832198.png#pic_center)

那么你本地的项目需要拉取下才能分支也得到更新：
![](https://img-blog.csdnimg.cn/4b1363f04c3b4ddeb5b11447e52a9098.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)



