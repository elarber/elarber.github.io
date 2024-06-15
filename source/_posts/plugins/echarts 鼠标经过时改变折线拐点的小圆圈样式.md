---
title: echarts 鼠标经过时改变折线拐点的小圆圈样式

index_img: https://img-blog.csdnimg.cn/20190929100816701.png
lazyload: true
categories:
- 前端插件使用
tags:
- echarts



---














![](https://img-blog.csdnimg.cn/20190926152718608.png)

> series: [
              {
                type: 'line',
                // symbol:'circle',    // 折线点设定为实心点
                symbolSize: 9,   // 设定折线点的大小
                label: {
                  normal: {
                    // show: true, // 折线上的文字是否显示
                    position: 'top'
                  }
                },
                // 折线条的样式
                lineStyle: {
                  color: "#3aa7ff",
                  width: 2
                }, 
                // 折线拐点的样式
                itemStyle: {
                  normal: { // 静止时：
                    color: '#3aa7ff' 
                  },
                  emphasis:{ // 鼠标经过时：
                    color: '#3aa7ff',
                    borderColor: '#3aa7ff'
                  }
                },
                // 填充区域的样式
                areaStyle: {
                  normal: {
                    // 填充色渐变
                    color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                      { offset: 0, color: "rgba(58, 167, 255,0.3)" },
                      { offset: 0.5, color: "rgba(58, 167, 255,0.2)" },
                      { offset: 1, color: "rgba(58, 167, 255,0)" }
                    ])
                  }
                },
                data: myTroughputChartsData.map(Number)
              }
            ]

此时空心圆变成实心圆了：
![](https://img-blog.csdnimg.cn/20190929100816701.png)
