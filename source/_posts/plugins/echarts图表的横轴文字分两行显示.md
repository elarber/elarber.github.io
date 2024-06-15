---
title: echarts图表的横轴文字分两行显示

index_img: https://img-blog.csdnimg.cn/20190919180157233.png
lazyload: true
categories:
- 前端插件使用
tags:
- echarts



---













X轴文字一行显示？
![](https://img-blog.csdnimg.cn/20190919180157233.png)
那么横坐标的数据用`map()`函数遍历，用[repalce()](https://blog.csdn.net/qq_42618566/article/details/101051990)替换那个空格字符：

```
data: ['09/19 周一', '09/20 周二', '09/21 周三', '09/22 周四', '09/23 周五', '09/24 周六', '09/25 周日'].map(function (str) {
   return str.replace(' ', '\n')
})
```

如图：
![](https://img-blog.csdnimg.cn/20190919151402946.png)
那么就实现横坐标的数据换行显示了：
![](https://img-blog.csdnimg.cn/20190919180107349.png)