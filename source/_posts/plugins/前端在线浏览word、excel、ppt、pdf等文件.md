---
title: 前端在线浏览word、excel、ppt、pdf等文件
index_img: https://img-blog.csdnimg.cn/4784cce8c10f434aab985938cba5d5c5.png
lazyload: true
categories:
- 前端插件使用
tags:
- word
- excel
- ppt
- pdf



---














> 使用接口：http://view.officeapps.live.com/op/view.aspx?src=<文档位置>



# word：
 [https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2F501351981.github.io%2Fvue-office%2Fexamples%2Fdist%2Fstatic%2Ftest-files%2Ftest.docx&wdOrigin=BROWSELINK](https://view.officeapps.live.com/op/view.aspx?src=https://501351981.github.io/vue-office/examples/dist/static/test-files/test.docx&wdOrigin=BROWSELINK)

![](https://img-blog.csdnimg.cn/66c48b8dcb4149e887f35a45e9fa41de.png)




# excel：
[https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2F501351981.github.io%2Fvue-office%2Fexamples%2Fdist%2Fstatic%2Ftest-files%2Ftest.xlsx&wdOrigin=BROWSELINK](https://view.officeapps.live.com/op/view.aspx?src=https://501351981.github.io/vue-office/examples/dist/static/test-files/test.xlsx&wdOrigin=BROWSELINK)

![](https://img-blog.csdnimg.cn/e94533b8d8c04a1a86d32a24bafb4d60.png)



# pdf：
- 办法1:[https://api.boot.jeecg.com/generic/web/viewer.html?file=https%3A%2F%2Fjeecgos.oss-cn-beijing.aliyuncs.com%2Ffiles%2Fsite%2Fjava_p3c.pdf](https://api.boot.jeecg.com/generic/web/viewer.html?file=https://jeecgos.oss-cn-beijing.aliyuncs.com/files/site/java_p3c.pdf)
![](https://img-blog.csdnimg.cn/28bb0cf84ae54a3cbedcf4d8a5e7a1c9.png)


- 办法2: `<a href="https://jeecgos.oss-cn-beijing.aliyuncs.com/files/site/java_p3c.pdf">打开</a>` href直接放文件地址就行
![](https://img-blog.csdnimg.cn/4784cce8c10f434aab985938cba5d5c5.png)


- 办法3
`<embed src="https://jeecgos.oss-cn-beijing.aliyuncs.com/files/site/java_p3c.pdf" type="application/pdf" style="width:100vw; height:100vh">` src直接放文件地址就行
但是embed兼容性可能没那么好


