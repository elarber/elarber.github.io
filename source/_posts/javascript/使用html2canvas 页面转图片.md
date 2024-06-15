---
title: 使用html2canvas 页面转图片

index_img: https://img-blog.csdnimg.cn/20200526163713924.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---











![使用html2canvas 页面转图片](https://img-blog.csdnimg.cn/20200526163713924.gif#pic_center)


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>页面转图片</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.4.1/dist/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
    <script src="https://cdn.bootcss.com/html2canvas/0.4.1/html2canvas.js"></script>
    <style type="text/css">
        .modal-body canvas{
            width: 100%;
            box-shadow: 0 0 12px #d1d1d1;
        }
    </style>
</head>
<body>
    <button id="save" type="button" class="btn btn-primary" data-toggle="modal" data-target=".bd-example-modal-xl">点击生成图片</button>
    <!-- 转图片的根容器 -->
    <div id="to-img" style="background-color: #f9eeee;">
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
        <h2>页面转图片的内容</h2>
    </div>
    <!-- 保存页面转图片的模态框 -->
    <div class="modal fade bd-example-modal-xl" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-xl modal-dialog-scrollable" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">页面转图片:</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <!-- 转图片后放这了 -->
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary" data-dismiss="modal">Save</button>
          </div>
        </div>
      </div>
    </div>











    <!-- 依赖 -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.4.1/dist/jquery.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.4.1/dist/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
    <!-- 转图片的逻辑 -->
    <script>
        document.querySelector("#save").onclick=function(event) {
            html2canvas(document.querySelector("#to-img"),{
                onrendered: function(canvas) {
                    document.querySelector(".modal-body").appendChild(canvas); //生成canvas标签
                    /*
                    // 创建img标签
                    let image = new Image();
                    image.src = canvas.toDataURL("image/png");
                    document.querySelector(".modal-body").appendChild(image);
                    return image;*/
                }
            })
        };
    </script>
</body>
</html>
```


