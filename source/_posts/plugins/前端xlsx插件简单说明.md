---
title: 

index_img: https://img-blog.csdnimg.cn/177e7afc704a4f1fb58529908d751205.png
lazyload: true
categories:
- 前端插件使用
tags:
- xlsx



---











### 单元格对象(Cell Object)
- !ref：单元格范围
- !rows：表格行属性
- !cols：单元格属性
- !merges：单元格合并
![](https://img-blog.csdnimg.cn/eaa4e20477cb44cc97313f6ea710c3ee.png)


### 单元格对象(Cell Object)
可以使用单元格对象来实现对单元格样式对修改,最终导出是一定要使用**xlsx-style**的方法导出
A1/B1/C1...  对应excel中的每一个具体的单元格

| key | 简介 |
|--|--|
| v | 原始值（有关更多信息，请参见“数据类型”部分） |
| w | 格式化文本（如果适用) |
| t | 单元格类型：b布尔值，n数字，e错误，s字符串，d日期 |
| f | 单元格公式（如果适用） |
|  r| 富文本编码（如果适用） |
| h | 富文本格式的HTML呈现（如果适用） |
| c | 与单元格相关的评论** |
| z | 与单元格关联的数字格式字符串（如果要求） |
| l | 单元超链接对象（.Target包含链接，.tooltip为工具提示） |
| s | 单元格的样式/主题（如果适用） |

![](https://img-blog.csdnimg.cn/177e7afc704a4f1fb58529908d751205.png)
s：样式
![](https://img-blog.csdnimg.cn/2b1ca88f94c443f18419d8e1d77128ed.png)



> [案例](https://blog.csdn.net/qq_42618566/article/details/107253501)、[表头表体自适应](https://ask.csdn.net/questions/7839639)

