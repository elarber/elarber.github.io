---
title: css文本超出换行

index_img: https://img-blog.csdnimg.cn/2019091815455366.png
lazyload: true
categories:
- css


tags:
- css

---







**先是这样的：**
![](https://img-blog.csdnimg.cn/2019091815455366.png)
#### 添加：`word-wrap: break-word`后：
![](https://img-blog.csdnimg.cn/2019091815450888.png)
**兼容性：**
![](https://img-blog.csdnimg.cn/20190918154755890.png)

或者：

```css
text-align: justify;
text-justify: newspaper;
word-break: break-all;
```



