---
title: CSS flex弹性布局

index_img: https://img-blog.csdnimg.cn/20200114130540351.png
lazyload: true
categories:
- css


tags:
- css

---




设置为弹性布局：
> display: flex;


**搭配以下属性和值，实现完美布局**
- #### ==flex-direction==：决定主轴的方向

取值：
 1. `row`：横排，从**左**到**右**。 **默认**
 2. `row-reverse`：横排，从**右**到**左**。
 3. `column`：竖排，从**上**到**下**。
 4. `column-reverse`：竖排。从**下**到**上**。
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114130540351.png)
示例：

	```css
	flex-direction: row;
	```

---


-  #### ==flex-wrap==：一条轴线排不下如何换行

取值：
1. `nowarp`：不换行，在一行显示。 **默认**
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114130818219.png)
2. `warp`：内容超过后换行，第一行在上方
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114130854983.png)

3. `warp-reverse`：换行后有两条轴线，reverse就是把轴线排列的顺序倒过来，第一行在下方。
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114130912715.png)

	示例：
	```css
	flex-wrap: nowarp;
	```

	> 以上flex-direction属性和flex-wrap属性**可以合成一个属性来设置**：`flex-flow`，属性值为两位
	> *语法：*`flex-flow: flex-direction的取值范围 flex-wrap的取值范围;`


---


-  #### ==justify-content== 定义横排的对齐方式：
取值：

1. `flex-start`：左对齐 **默认**
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114131420789.png)

2. `flex-end`：右对齐
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114131426297.png)

3. `center`：居中
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114131459717.png)

4. `space-between`：两端顶边平均散开，项目与项目之间的间隔都相等。
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114131452443.png)

5. `space-around`：平均散开。项目与项目之间的间隔比项目与边框的间隔大一倍。
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200114131512991.png)

	示例：

	```css
	justify-content: flex-start;
	```

---



-  #### ==align-items== 定义竖排对齐方式：
取值：
1. `stretch`：

2. `flex-start`：上对齐 **默认**
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200121113808318.png)

3. `flex-end`：下对齐
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200121113829606.png)

4. `center` ：中心对齐
![CSS flex弹性布局](https://img-blog.csdnimg.cn/20200121113843262.png)

5. `baseline`：基线对齐


	示例：

	```css
	align-items: flex-start;
	```

---



-  #### ==align-content== 多根轴线对齐方式：
取值：
1. `stretch`：拉伸

2. `flex-start` ：start侧开始，上对齐

3. `flex-end`：end侧开始，下对齐

4. `center`：中心对齐

5. `space-between`：上下没有间距，中间各子元素间距相同

6. `space-around`：上下间距之和等于中间各个间距

	示例：

	```css
	align-content: stretch;
	```











