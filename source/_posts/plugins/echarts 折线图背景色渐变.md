---
title: echarts 折线图背景色渐变

index_img: https://img-blog.csdnimg.cn/20190916145640101.png
lazyload: true
categories:
- 前端插件使用
tags:
- echarts



---











```
// 填充区域的样式
          areaStyle: {
            normal: {
              // 填充色渐变
              color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                { offset: 0, color: "#3aa7ff" },
                { offset: 0.5, color: "rgba(58, 167, 255,0.4)" },
                { offset: 1, color: "rgba(58, 167, 255,0)" }
              ])
            }
          },

```

![](https://img-blog.csdnimg.cn/20190916145640101.png)

**效果图：**
![](https://img-blog.csdnimg.cn/20190916145707606.png)

