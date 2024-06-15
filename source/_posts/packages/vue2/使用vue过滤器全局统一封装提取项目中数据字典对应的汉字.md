---
title: 使用vue过滤器全局统一封装提取项目中数据字典对应的汉字

index_img: https://img-blog.csdnimg.cn/4ce63962dfc54b449863a17979af0312.png
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- 过滤器


---












# 使用场景
- 项目中的下拉菜单太多
![](https://img-blog.csdnimg.cn/4ce63962dfc54b449863a17979af0312.png)

- 重点是返回的数据是对应的码，那么每个页面都要v-if 1234...写吗？
![](https://img-blog.csdnimg.cn/57caa2f79b8941b2b77cae085ed3a370.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)

那太臃肿了，不如统一处理
# 解决方案
那么我们可以封装个[全局过滤器](https://quanyi.blog.csdn.net/article/details/107784878)，用于灵活转数据字典的对应文字

```javascript
// 文本化数据
export function tansfortext(value, dictionaries = [], config = { name: "code_name", value: "code_value" }) {
  // console.log(value, dictionaries, config);
  if (!value) {
    // console.log("没有字典值");
    return value;
  }
  if (dictionaries.length === 0) {
    // console.log("没有字典集");
    return value
  }
  // 字典没有code_name，但取key还是code_name
  if (!Object.hasOwn(dictionaries[0], "code_name") && config.name === "code_name") {
    console.log(value, "没有对应的字典name");
    return value;
  }




  value = value.toString()
  // 如果是,隔开的字符串多值转义
  if (value.includes(",")) {
    let data = [];
    for (let item of value.split(",")) {
      data.push(dictionaries.find(it => {
        return it[config.value] === item
      }));
    }
    return data.map(item => {
      return item[config.name]
    }).join(",")
  } else {
    // 如果是单值转义
    const data = dictionaries.find(item => {
      return item[config.value] === value
    });
    return data ? data[config.name] : value;
  }
}

// 数字千位符
export function toThousands(num) {
  if (isNaN(num)) {
    return num
  }

  num = parseFloat(num);
  num = num.toFixed(2);
  const reg = /\B(?=(\d{3})+(?!\d))/g; // 逢3位,
  return num.replace(reg, ',');
}

```



# 使用
将该字典的整条数据传过去就会提取对应的汉字啦
![](https://img-blog.csdnimg.cn/e4f25684cf094987ae8eb89474e20c72.png)



---
**或者：**

> # 也可以直接安装个[工具](https://www.npmjs.com/package/code-transfor-text_vue)

```bash
npm install code-transfor-text_vue
```

![](https://img-blog.csdnimg.cn/07f88c8b98af40459d8b1ab5b1a6a94e.png)







