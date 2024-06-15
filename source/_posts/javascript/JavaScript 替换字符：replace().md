---
title: JavaScript 替换字符：replace()

index_img: 
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---












**定义：**

> 用于在字符串中替换另一些字符，或替换一个与正则表达式匹配的子串。

**语法：**

> stringObject.replace(被替换的正则或字符，要替换成的字符)

**例子：**

```
<script>

  var str="Visit Microsoft!"
  document.write(str.replace(/Microsoft/, "W3School"));	// 会输出：Visit W3School!

</script>
```

