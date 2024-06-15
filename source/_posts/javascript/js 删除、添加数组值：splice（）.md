---
title: js 删除、添加数组值：splice（）

# index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











**语法：**
删除：
```javascript
数组.splice(位置,删几个)
```

删除并添加：删几个位0时表示不删除。

```javascript
数组.splice(位置,删几个，添加的)
```

**示例：**
```javascript
<script type="text/javascript">
var arr = ["George","John","Thomas","James","Adrew","Martin"];
console.log(arr.splice(2,1,"William"));	// 删除第二个元素，并添加一个新元素来替代被删除的元素

// 会输出： George,John,William,James,Adrew,Martin

</script>
```


