---
title: js 获取电脑(手机)的电池信息

index_img: https://img-blog.csdnimg.cn/20200403141410423.png
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











![js 获取电脑(手机)的电池信息](https://img-blog.csdnimg.cn/20200403141410423.png)


```javascript
navigator.getBattery().then(res=>{
	console.log(res);
});
```



| 字段 | 解释 | 操作 |
|:-- |-- |-- |
| charging | 是否在充电 | 只可读  |
| chargingTime | 若在充电，那么还需充电的事件 | 只可读    |
| dischargingTime| 剩余电量 |  只可读   |
| level| 剩余电量的百分数(小数) | 只可读    |
| onchargingchange| 监听充电状态的改变 | 监听事件  |
| onchargingtimechange| 监听充电时间的改变 | 监听事件  |
| ondischargingtimechange| 监听电池可用时间的改变 | 监听事件  |
| onlevelchange| 监听剩余电量百分数的改变 |  监听事件 |



