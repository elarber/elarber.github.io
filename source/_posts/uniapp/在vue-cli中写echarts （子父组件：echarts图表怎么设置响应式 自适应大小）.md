---
title: 在vue-cli中写echarts （子父组件：echarts图表怎么设置响应式 自适应大小）

index_img: https://img-blog.csdnimg.cn/20190919141651603.png
lazyload: true
categories:
- vue2


tags:
- vue2
- web



---





是用子父组件式写的：
**父组件：**
```
<template>
  <div class="index2">
      <p slot="title" class="title">我的处理量</p>
      <Mydisposes ref="myChange" />
  </div>
</template>

<script>
import Mydisposes from './ECharts/mydisposes'; // 引入子组件：我的处理量

export default {
  name: 'index2',
  data () {
    return {
     
    }
  },
  components: {
    Mydisposes
  },
  mounted () {
    window.onresize = () => {
      this.$refs.myChange.my() // 调用子组件的功能 - 图表伸缩响应
    }
  }
}
</script>

<style lang="less" scoped>

</style>

```

---
**子组件：**

```
<template>
  <div class="mydisposes">
    <p style="text-align: right; margin-bottom:20px;"><Icon type="ios-square" style="color: #55C926;" /> 我的累计处理量: <b style="font-size: 20px;">{{ mydisposesNum }}</b>件</p>
    <div ref="mydisposesecharts" style="width: 100%; height: 400px;"></div>
  </div>
</template>

<script>
import echarts from 'echarts'

export default {
  name: 'mydisposes',
  data () {
    return {
      mydisposesNum:'2,037',
      mydisposesecharts: null,
      echartsData: [77, 89, 97, 56, 102, 91, 121]
    }
  },
  methods: {
    my() {  // 此功能需在父组件上执行
      this.mydisposesecharts.resize();  // 重载图表（图表伸缩响应）
    }
  },
  created () {
    
  },
  mounted () {
    const option = {
     /*  title: {
        show:true,
        text: '趋势图 - 主标题',
        subtext:'我是副标题',
        right:0,
      },
      // 工具箱
      toolbox:{
        show:true,
        feature:{
            dataView:{
                show:true
            },
            restore:{
                show:true
            },
            dataZoom:{
              show:true
            },
            saveAsImage:{
              show:true
            },
            magicType:{
              type:['line','bar']
            }
        }
      }, */
     // 鼠标经过图表时的悬浮框
            tooltip: {
              trigger: 'axis',
              confine:true,
              backgroundColor: '#CFCFD3',
              axisPointer:{
                lineStyle:{
                  color:'#3aa7ff'
                }
              },
              formatter: function (params, ticket, callback) {
                // console.log(params);
                let date=new Date();
                let year=date.getFullYear();
                let showText = year +'-'+ params[0].axisValueLabel.replace('/', '-').substring(0, params[0].axisValueLabel.length-2) +'<br>' + '办件处理量：'+ params[0].value;
                if(showText.substring(0,7)==year+'-今天'){
                  showText = '今天' +'<br>' + '办件处理量：'+ params[0].value;
                }
                return showText;
              },
              textStyle:{
                color: '#31394D' // 提示悬浮层的文字颜色
              }
            },
            // 图表的边距
            grid: {
              top: '10px',
              left: '10px',
              right: '20px',
              bottom: '10px',
              containLabel: true
            },
            xAxis: [
              {
                type: 'category',
                boundaryGap: false,
                axisTick: {
                  show:false // 是否显示坐标轴刻度。
                }, 
                axisLine:{
                  lineStyle: {
                    color: '#748AA1', // 轴线颜色
                  }
                },
                axisLabel: {  // 横轴的文字样式
                  lineHeight: 18,
                  color: '#748AA1',
                  fontSize : 14
                },
                data: myMergeWeekDate
                      .map(function (str) {
                        return str.substring(5, str.length)  // 截掉字符串，前5位不要
                      }).map(function (str) {
                         return str.replace('-', '/');  // 将日期中的 - 替换为 /
                      }).map(function (str) {
                        return str.replace(' ', '\n')  // 将日期中的空格替换为：换行
                      }).map(function (str) {
                        return str.replace('周天', '周日')  // 将日期中的周天替换为：周日
                      }).map(function (str) {
                        return str.replace(monthDay, '今天')  // 将当天数字改为：今天
                      })
              }
            ],
            yAxis: [
              {
                type: 'value',
                minInterval: 1, // 设置成1：保证纵轴数字显示成整数。
                axisLine: {
                  show:false, // 是否显示坐标轴轴线。
                }, 
                axisTick: {
                  show:false // 是否显示坐标轴刻度。
                }, 
                splitLine: {
                  show: true,
                  lineStyle:{
                    type:'dashed', // 背景线为虚线
                    color:'#C5D9E8'
                  }
                },
                axisLabel: {  // 纵轴的文字样式
                  color: '#3F536E',
                  fontSize : 14,
                  margin: 18  // 文字与折线图的间距
                },
              }
            ],
            series: [
              {
                type: 'line',
                // symbol:'circle',    // 折线点设定为实心点
                symbolSize: 9,   // 设定折线点的大小
                label: {
                  normal: {
                    // show: true, // 折线上的文字是否显示
                    position: 'top'
                  }
                },
                // 折线条的样式
                lineStyle: {
                  color: "#3aa7ff",
                  width: 2
                }, 
                // 折线拐点的样式
                itemStyle: {
                  normal: { // 静止时：
                    color: '#3aa7ff' 
                  },
                  emphasis:{ // 鼠标经过时：
                    color: '#3aa7ff',
                    borderColor: '#3aa7ff'
                  }
                },
                // 填充区域的样式
                areaStyle: {
                  normal: {
                    // 填充色渐变
                    color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                      { offset: 0, color: "rgba(58, 167, 255,0.3)" },
                      { offset: 0.5, color: "rgba(58, 167, 255,0.2)" },
                      { offset: 1, color: "rgba(58, 167, 255,0)" }
                    ])
                  }
                },
                data: myTroughputChartsData.map(Number)
              }
            ]
    }
    this.$nextTick(() => {
      this.mydisposesecharts = echarts.init(this.$refs.mydisposesecharts)
      this.mydisposesecharts.setOption(option)
      // this.mydisposesecharts.on('resize',window, this.resize)
    })
  },
  beforeDestroy () {
    // off(window, 'resize', this.resize)
  }
}
</script>

<style lang="less" scoped>

</style>

```

效果如下：
![](https://img-blog.csdnimg.cn/20190919141651603.png)
