---
title: echarts实现中国地图下钻进入下一级行政区(地图钻取)

index_img: https://img-blog.csdnimg.cn/6193933ec89b4817a9433d65c0082432.gif
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2



---











![](https://img-blog.csdnimg.cn/6193933ec89b4817a9433d65c0082432.gif#pic_center)

# 获取geo数据：

> 可以使用[node爬虫](https://gitee.com/gitee-cherry/get-geoData)获取数据

最好多爬几遍，因为有时候会获取错误



# 实现逻辑
拥有geo数据后
1. 请求geo数据
2. 注册地图 registerMap
3. 配置echarts
4. 增加事件监听（点击事件）

如果点击了，回到第一步。功能就是循环以上4步逻辑


# echarts实现
## html

```html
  <div ref="echarts-dom" class="echarts-content"></div>
```


## js:

```javascript
export default {
  data() {
    return {
      mapChart: null,
      addressCode: []
    };
  },
  mouted(){
    this.mapChart = echarts.init(this.$refs["echarts-dom"]);
    this.getData();
  },
  methods: {
    getData("100000") {
	  fetch(`${process.env.VUE_APP_ORIGIN}/geoData/${code}.json`)
	     .then((res) => {
	       return res.json();
	     }).then((res) => {
	       this.addressCode = res.features;
	       echarts.registerMap("echartsMap", res);
	       this.setEchartsOptions();
	     })
	     .finally((err) => {
	       this.mapLoading = false;
	     });
	  },
	 // echarts配置
     setEchartsOptions() {
       this.mapChart.off("click"); //图表渲染前销毁点击事件
       this.mapChart.setOption({
          series: [
            {
              type: "map",
              mapType: "echartsMap",
              roam: true,
              scaleLimit: {
                min: 1.1,
                max: 5.2,
              },
              data: this.addressCode,
              // 地图模块样式
              itemStyle: {
                // 默认模块样式
                normal: {
                  borderWidth: 1.3,
                  borderColor: "#00ffff",
                  areaColor: "#09295b",
                },
                // 鼠标经过模块样式
                emphasis: {
                  show: true,
                  borderWidth: 3,
                  areaColor: "#0d559d",
                  label: {
                    show: true,
                    textStyle: {
                      color: "#fff",
                    },
                  },
                },
              },
              label: {
                show: true,
                textStyle: {
                  color: "#fff",
                },
              },
            },
          ],
        },true);
      this.addEchartsEventListener();
    },
    // 监听echarts事件
    addEchartsEventListener() {
      const that = this;
      // 点击时间
      this.mapChart.on("click", function (params) {
        console.log(params.data);
        that.getData(params.data.codeNumber);
      });

      // 移动 | 缩放
      this.mapChart.on("georoam", (params) => {
        that.$emit("swicthPanle", false);
      });
    },
  }
}
```



