---
title: Object.hasOwn()：判断该对象是否有某个属性

index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











#### 定义：判断该对象是否有某个`指定的`自定义属性。 ==不包含==继承原型链的属性


>  - 返回值： 返回一个布尔值， 判断该对象有指定的属性，就会返回`true`，没有就返回`false` ；
>  - 语 法：`Object.hasOwn(Object,'prop') `

 
 示列：
```javascript
var obj = {
    a: 1,
    fn: function(){
 
    },
    c:{
        d: 5
    }
};
console.log(Object.hasOwn(obj, 'a'));  // 此处返回true
console.log(Object.hasOwn(obj, 'fn')); // 此处返回 true
console.log(Object.hasOwn(obj, 'c'));  // 此处返回 true
console.log(Object.hasOwn(obj, 'd'));  // 此处返回 true
console.log(Object.hasOwn(obj, 'd'));  // 此处返回 false, 因为obj对象没有d属性
 
var str = new String();
// split方法是String这个对象的方法，str对象本身是没有这个split这个属性的
console.log(str.hasOwnProperty('split'));  // 此处返回false
console.log(String.prototype.hasOwnProperty('split'));  // 此处返回true
```


