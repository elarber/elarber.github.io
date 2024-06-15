---
title: html技术： 用svg标签画图

index_img: https://img-blog.csdnimg.cn/20200403183258687.png
lazyload: true
categories:
- css


tags:
- css

---





如同`canvas`一样，`svg`标签是个画布(容器)，用来放图

```html
<!--	必须初始化宽高，要不然看不见了	  -->
<svg width="600px" height="400px">
	<!--	放画的图	  -->
</svg>
```

---

#### 输出直线：`<line />`
![html svg画图](https://img-blog.csdnimg.cn/20200403183258687.png)

效果：
![html svg画图](https://img-blog.csdnimg.cn/20200403182839725.png)


#### 输出折线：`<polyline />`
![html svg画图](https://img-blog.csdnimg.cn/20200403190239906.png)![html svg画图](https://img-blog.csdnimg.cn/20200403190322285.png)


#### 输出文本：`<text />`
![html svg画图](https://img-blog.csdnimg.cn/20200403183532169.png)


![html svg画图](https://img-blog.csdnimg.cn/2020040318345397.png)


#### 输出矩形：`<rect />`
![html svg画图](https://img-blog.csdnimg.cn/20200403183742713.png)

![html svg画图](https://img-blog.csdnimg.cn/2020040318364082.png)

#### 输出多边形：`<polygon />`
![html svg画图](https://img-blog.csdnimg.cn/20200403191245581.png)

![html svg画图](https://img-blog.csdnimg.cn/20200403191010411.png)


#### 输出正圆：`<circle />`
![html svg画图](https://img-blog.csdnimg.cn/20200403184217318.png)

![html svg画图](https://img-blog.csdnimg.cn/20200403184229421.png)


#### 输出椭圆：`<ellipse />`
![html svg画图](https://img-blog.csdnimg.cn/20200403184616461.png)

![html svg画图](https://img-blog.csdnimg.cn/20200403184626221.png)

#### `path`标签画线：`<path />`
![html svg画图](https://img-blog.csdnimg.cn/20200403192751979.png)

![html svg画图](https://img-blog.csdnimg.cn/20200403192803426.png)

参数除了除了 M L  还有 H V Z A（也区分大小写）
如 v h：
![html svg画图](https://img-blog.csdnimg.cn/20200403193055398.png)
![html svg画图](https://img-blog.csdnimg.cn/20200403193104587.png)
**` path ` 不止可以画直线，还可以画 ==弧线==：**

![](https://img-blog.csdnimg.cn/20200403193359710.png)

![html svg画图](https://img-blog.csdnimg.cn/2020040319340712.png)

