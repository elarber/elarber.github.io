---
title: vue2 全局批量注册过滤器 filters

index_img: https://img-blog.csdnimg.cn/20200804135112819.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web
- 过滤器


---





![vue 全局批量注册过滤器](https://img-blog.csdnimg.cn/20200804135112819.png)

```javascript
export default {
  numberFormatter: (num, digits) => {
    const si = [
      { value: 1E18, symbol: 'E' },
      { value: 1E15, symbol: 'P' },
      { value: 1E12, symbol: 'T' },
      { value: 1E9, symbol: 'G' },
      { value: 1E6, symbol: 'M' },
      { value: 1E3, symbol: 'k' }
    ]
    for (let i = 0; i < si.length; i++) {
      if (num >= si[i].value) {
        return (num / si[i].value).toFixed(digits).replace(/\.0+$|(\.[0-9]*[1-9])0+$/, '$1') + si[i].symbol
      }
    }
    return num.toString()
  },

  tranForm(data) {
    switch (data) {
      case "1":
        return "哈哈";
      case "2":
        return "丫丫";
      case "3":
        return "拉拉";
      case "4":
        return "大大阿达";
    }
  }
}
```

![vue 全局批量注册过滤器](https://img-blog.csdnimg.cn/2020080413515630.png)

```javascript
import one from './one'
import two from './two'

const filters = {
  one, two
}
export default {
  install(Vue) {
    Object.keys(filters).forEach(key => {
      for (let i in filters[key]) {
        Vue.filter(i, filters[key][i])
      }
    })
  }
}
```


![vue 全局批量注册过滤器](https://img-blog.csdnimg.cn/20200804135235445.png)

```javascript
import filters from './filters/index'


Vue.use(filters);
```


使用过滤器：
![vue 全局批量注册过滤器](https://img-blog.csdnimg.cn/20200804140100583.png)

---



> # 案例
> [https://quanyi.blog.csdn.net/article/details/124142095](https://quanyi.blog.csdn.net/article/details/124142095)
