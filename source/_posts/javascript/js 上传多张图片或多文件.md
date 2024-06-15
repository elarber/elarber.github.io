---
title: js 上传多张图片或多文件

index_img: https://img-blog.csdnimg.cn/2019111215152673.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---













```html
<!Doctype>
<html>
	<head>
		<meta charset="utf-8">
		<title>上传多张图片</title>
		<style>
			.upload-pic{ width: 120px;  height: 30px;  line-height: 30px; border-radius: 4px; color: #fff; position: relative; cursor: pointer;
                font-size: 14px;  background-color: #44b549;  text-align: center;  display: inline-block;
                vertical-align: middle; margin-left: 8px;  margin-top: 8px;  }
            .upload-pic .up-lab,.upload-pic .up-file{ width: 100%; height: 100%; position: absolute; left: 0; top: 0; z-index: 2; overflow: hidden;}
            .upload-pic .up-lab{ background-color: #44b549; cursor: pointer; }
            .upload-pic .up-file{ z-index: 1;}

            .group-coms-pic{ padding-top: 30px; overflow: hidden; }
            .group-coms-pic .item{  width: 116px; height: 148px; border:1px solid #f0f0f0; position: relative; float: left; overflow: hidden; margin-right: 20px; margin-bottom: 20px; }
            .group-coms-pic .pic-box{ width:118px; height:117px; border-bottom:1px solid #f0f0f0;  position: relative;}
            .group-coms-pic .pic-box .deletephotos {
              position: absolute;
              right: 4px;
              z-index: 10;
              background: #76d767;
              margin: 0;
              color: white;
              font-size: 26px;
              padding: 0 9px;
            }
            .group-coms-pic .pic-box .deletephotos:hover{
              background-color: white;
              border: 1px solid #76d767;
              color: #76d767;
            }
            .group-coms-pic .pic-box .img{ height:117px; position: absolute; left: 50%; top: 50%;
                transform:translate(-50%,-50%);}
            .group-coms-pic .tk{ padding:0 9px; height: 32px; line-height: 32px; text-align: left;
                overflow: hidden;  white-space: nowrap;  text-overflow: ellipsis; color: #353535;  font-size: 14px;}
		</style>
	</head>
	<body>
        <div class="upload-pic">
          <label class="up-lab" for="add-pic-btn">点击此处上传图片</label>
          <input type="file" accept="image/*" multiple class="up-file" id="add-pic-btn">
        </div>
        <div class="group-coms-pic" id="groupTu">
          <div class="item">
            <div class="pic-box">
              <button title="点击取消上传本图" class="deletephotos btn"> &times; </button>
              <img class="img"
                src="http://n4-q.mafengwo.net/s13/M00/9E/31/wKgEaVx6eymAKYK_AAU40faE3IY94.jpeg?imageMogr2%2Fthumbnail%2F%21300x166r%2Fgravity%2FCenter%2Fcrop%2F%21300x166%2Fquality%2F100">
            </div>
            <div class="tk">111.jpg</div>
          </div>
        </div>


 
		<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
		<script>
			 //上传多个文件方法
            document.getElementById("add-pic-btn").addEventListener("change", function () {
              var obj = this,
                length = obj.files.length,
                arrTitle = []; //存标题名
              _html = '';

              for (var i = 0; i < length; i++) {
                var reader = new FileReader();
                if (!reader) {
                  console.log('对不起，您的浏览器不支持！请更换浏览器试一下');
                  return
                }
                //存储上传的多张图片名字
                arrTitle.push(obj.files[i].name)

                reader.error = function (e) {
                  console.log("读取异常")
                };
                //iffi语法
                (function (i) {
                  //读取成功
                  reader.onload = function (e) {
                    //console.log(e)
                    var _src = e.target.result;
                    //创建节点元素
                    var divItem = document.createElement('div');
                    divItem.setAttribute('class', 'item');

                    var divPic = document.createElement('div');
                    divPic.setAttribute('class', 'pic-box');

                    var dePhotosBTN = document.createElement('button');
                    dePhotosBTN.setAttribute('class', 'deletephotos btn');
                    dePhotosBTN.setAttribute('title', '点击取消上传本图');
                    dePhotosBTN.innerHTML = '&times;'
                    divPic.setAttribute('class', 'pic-box');

                    var img = document.createElement('img');
                    img.setAttribute('class', 'img');
                    img.setAttribute('src', _src);

                    var divTk = document.createElement('div');
                    divTk.setAttribute('class', 'tk');
                    divTk.setAttribute('title', arrTitle[i]);
                    divTk.innerHTML = arrTitle[i];

                    // 插入该元素
                    divItem.appendChild(divPic);
                    divPic.appendChild(dePhotosBTN);
                    divPic.appendChild(img);
                    divItem.appendChild(divTk);

                    //增加节点
                    var groupTu = document.getElementById('groupTu');
                    groupTu.insertBefore(divItem, groupTu.firstChild);
                  };
                })(i)
                reader.onloadstart = function () {

                }
                reader.onprogress = function (e) {
                  if (e.lengthComputable) {
                    console.log("正在读取文件");
                  }
                };
                reader.readAsDataURL(obj.files[i]);
              }
            });
            // 删除图片
            $(".group-coms-pic").bind("DOMNodeInserted", () => {
              const deletePhotosBTN = document.querySelectorAll('.deletephotos');
              const photosBOX = document.querySelectorAll('.item');
              for (let i = 0; i < deletePhotosBTN.length; i++) {
                deletePhotosBTN[i].onclick = () => {
                  photosBOX[i].remove();
                }
              }
            });
		</script>
	</body>
</html>
```

![js 上传多张图片或多文件](https://img-blog.csdnimg.cn/20191112150445819.gif)


---
但目前存在个bug还没解决：
图片都删了再选就选不了了，为什么？😪
![js 上传多张图片或多文件](https://img-blog.csdnimg.cn/2019111215152673.gif)


