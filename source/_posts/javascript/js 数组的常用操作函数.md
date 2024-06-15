---
title: js 数组的常用操作函数

index_img: https://img-blog.csdnimg.cn/20200128231357805.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---










```javascript
	var array = ["jeiw","sfwe","fasfwe","ftqq","hjweq","jfoiwe"];
    var newArrray = ["qqq","www","eee","rrr","ttt","yyy"];
```

#### 1. concat()
- 连接一个或多个数组
- 返回连接后的新数组
	

	```javascript
	console.log(    array.concat(newArrray)    );
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128225356685.png)

---

#### 2. push()
- 从数组的后面添加数组
- 返回新数组的长度

	

	```javascript
	console.log(    array.push(newArrray)    );
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128225541394.png)

```javascript
	array.push(newArrray)
    console.log(array);
```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128230045844.png)



---



#### 3. unshift()
- 从数组的前面添加数组
- 返回新数组的长度
	


	```javascript
	console.log(array.unshift(newArrray));
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128232047497.png)

```javascript
	array.unshift(newArrray)
    console.log(array);
```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128231943212.png)


---

#### 4. join()
- 将数组变成字符串（默认是逗号分隔，可指定符号）
- 返回分割后的字符串
	

	```javascript
	console.log(    array.join(newArrray)    );
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128230534818.png)

```javascript
console.log(    array.join("-")    );
```
![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128230613812.png)


---



#### 5. pop()
- 删除数组的最后一个元素
- 返回被删除的元素
	

	```javascript
	console.log(array.pop());  
    console.log(array);
	```


![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128230934414.png)


---


#### 6. shift()
- 删除数组的第一个元素
- 返回被删除的元素
	

	```javascript
	console.log(array.shift());  
    console.log(array);
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128231357805.png)

---


#### 7. revarse()
- 反转数组的排序
- 返回反转后的数组
	

	```javascript
	console.log(array.reverse());
	```

![js 数组的常用操作函数](https://img-blog.csdnimg.cn/20200128232347729.png)



#### 8. includes()
- 判断是否包含该参数
- 返回true或false




```javascript
 let MSids = [
        "1000010000124855",
        "1000010000124856",
        "1000010000124857",
        "1000010000124858",
        "1000010000124860",
        "1000010000124861",
        "1000010000124863",
        "1000010000124865"
      ];
  if (MSids.includes("1000010000124861")) {
     console.log("包括")
   } else {
      console.log("不包括")
   }
```



[https://blog.csdn.net/qq_42618566/article/details/104664040](https://blog.csdn.net/qq_42618566/article/details/104664040)







