---
title: node爬取中国行政区域geo数据，生成本地json文件

index_img: https://img-blog.csdnimg.cn/2bde79cb01bb4e22af608c736e8ca48b.png
lazyload: true
categories:
- node
tags:
- node
- 爬虫



---













# 依赖

```bash
{
  "dependencies": {
    "axios": "^1.4.0",
    "colors": "^1.4.0",
    "express": "^4.18.2",
    "fs": "^0.0.1-security"
  }
}
```

# 数据来源

```bash
https://datav.aliyun.com/portal/school/atlas/area_selector
```


# 代码

```javascript
const axios = require('axios');
const fs = require("fs");
const colors = require('colors');






function getData(code="100000_full"){
  axios.get("https://geo.datav.aliyun.com/areas_v3/bound/"+code+".json").then(res=>{
    console.log('=========== 数据读取成功 ==========='.yellow);
    console.log(res.data);
    console.log('========== ============= =========='.yellow);

    /* -------------   生成json文件    --------------*/
    const writerStream = fs.createWriteStream("data/"+parseInt(code)+'.json');
    writerStream.write(JSON.stringify(res.data));
    writerStream.end();

    // 文件处理流事件：data, end, and error
    writerStream.on('finish', function () {
      console.log('<<<------------------------------- 写入完成 ------------------------------->>>\n'.green);
    });
    writerStream.on('error', function (err) {
      console.log('<<<------------------------------- 写入错误 ------------------------------->>>\n'.red);
    });

    // 下钻子项
    if(res.data.features.length>1){
      res.data.features.map(item => {
        if(item.properties.childrenNum){
          getData(item.properties.adcode+"_full")
        }else{
          getData(item.properties.adcode)
        }
      })
    }
  }).catch(err=>{
    console.log('========== 数据读取错误 =========='.red);
  })
};
getData();



// function throttled(fn, delay = 800) {
//   let timer = null;
//   return function (...args) {
//     if (!timer) {
//       timer = setTimeout(() => {
//         fn.apply(this, args)
//         timer = null
//       }, delay);
//     }
//   }
// }
```



# 结果
![](https://img-blog.csdnimg.cn/2bde79cb01bb4e22af608c736e8ca48b.png)


> [https://gitee.com/gitee-cherry/get-geoData](https://gitee.com/gitee-cherry/get-geoData)


