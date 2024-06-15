---
title: VS Code添加vue2的代码片段、作者信息

index_img: https://img-blog.csdnimg.cn/20200702124815113.png
lazyload: true
categories:
- 前端周边
tags:
- VS Code



---











## 打开设置
![](https://img-blog.csdnimg.cn/7fdd1cfb60014517a984001e2dc11767.png)

## 新建文件
![](https://img-blog.csdnimg.cn/17edd43e4c454e68ab67a4193f125fcb.png)

## 添加代码

```json
{
    "Print to console": {
        "prefix": "vue2",
        "body": [
            "<template>",
            "  <div class=\"$3\">",
            "    ",
            "  </div>",
            "</template>",
            "",
            "<script>",
            "/**",
            "* @author        全易",
            "* @time          ${CURRENT_YEAR}-${CURRENT_MONTH}-${CURRENT_DATE} ${CURRENT_HOUR}:${CURRENT_MINUTE}:${CURRENT_SECOND}  ${CURRENT_DAY_NAME}",
            "* @description   $1",
            "**/",
            "",
            "",
            "export default {",
            "  name: '$2',",
            "  data () {",
            "    return {",
            "      ",
            "    }",
            "  },",
            "  methods: {",
            "      ",
            "  }",
            "}",
            "</script>",
            "",
            "<style lang=\"less\" scoped>",
            "",
            "</style>"
        ],
        "description": "Log output to console"
    }
}
```

## 试试吧
![](https://img-blog.csdnimg.cn/5c4f53611d3f435888bd34853a3186c6.png)

如果不行就重启下编辑器

**按tab键切换光标悬停位置：**
![VS Code添加vue的代码片段、作者信息](https://img-blog.csdnimg.cn/20200702124815113.png)




---


# 代码块变量

> 常用变量
>     `TM_SELECTED_TEXT` 当前选中内容或空字符串
>     `TM_CURRENT_LINE` 当前行内容
>     `TM_CURRENT_WORD` 光标处字符或空字符串
>     `TM_LINE_INDEX` 从0开始的行号
>     `TM_LINE_NUMBER` 从1开始的行号
>     `TM_FILENAME` 当前被编辑文档名
>     `TM_FILENAME_BASE` 当前被编辑文档名，没有后缀
>     `TM_DIRECTORY` 当前被编辑文档目录
>     `TM_FILEPATH` 当前被编辑文档全路径
>     `CLIPBOARD` 当前剪切板内容
>     
>   ---
>   
> 日期和时间相关变量
>     `CURRENT_YEAR` 当前年
>     `CURRENT_YEAR_SHORT` 当前年后两位
>     `CURRENT_MONTH` 月份，两位数字表示，例如02
>     `CURRENT_MONTH_NAME` 月份全称，例如 'July'
>     `CURRENT_MONTH_NAME_SHORT` 月份简写 ，例如'Jul
>     `CURRENT_DATE` 某天
>     `CURRENT_DAY_NAME` 星期几， 例如'Monday')
>     `CURRENT_DAY_NAME_SHORT` 星期几的简写， 'Mon'
>     `CURRENT_HOUR` 小时，24小时制
>     `CURRENT_MINUTE` 分钟
>     `CURRENT_SECOND` 秒数

