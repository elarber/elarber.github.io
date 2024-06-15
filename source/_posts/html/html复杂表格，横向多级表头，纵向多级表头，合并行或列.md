---
title: html复杂表格，横向多级表头，纵向多级表头，合并行或列

index_img: https://img-blog.csdnimg.cn/20200807102014876.png
lazyload: true
categories:
- html
tags:
- html
- table
- 原生合并表格


---










![html复杂表格，横向多级表头，纵向多级表头](https://img-blog.csdnimg.cn/20200807102014876.png)


`th`或`td`标签有两个属性可用于占位：

> `rowspan="数字"` 表示该单元格占 ==n行==
> `colspan="数字"` 表示该单元格占 ==n列==


```html
 <table class="table" cellpadding="1" cellspacing="1" border="1">
	 <tr>
	     <th colspan="3" rowspan="2">用电分类</th>
	     <!-- colspan="2" 表示这一列占2列 -->
	     <th colspan="5">电度电价（含政府性基金及附加）</th>
	     <th colspan="2">基本电价</th>
	   </tr>
	   <tr>
	     <!-- rowspan="2" 表示这一列占3行 -->
	     <th>不满1千伏</th>
	     <th>1-10千伏</th>
	     <th>35-110千伏以内</th>
	     <th>110千伏</th>
	     <th>220千伏及以上</th>
	     <th>最大需量元/千瓦/月</th>
	     <th>变压器容量元/千伏安/月</th>
	   </tr>
	   <tr>
	     <th rowspan="4">城镇居民生活用电</th>
	     <th colspan="2">城市合表居民用电</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th rowspan="3">城市一户一表居民用电</th>
	     <th>月用电量180千瓦时及以内部分</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th>月用电量180千瓦至280千瓦时部分</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th>月用电量超280千瓦时部分</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th colspan="3">一般工商业及其他用电</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th colspan="3">大工业用电</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th colspan="3">农业生产用电</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	   <tr>
	     <th colspan="3">其中：贫困县农业排灌用</th>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	     <td>13123</td>
	   </tr>
	 </table> 
```






