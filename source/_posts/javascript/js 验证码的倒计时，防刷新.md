---
title: js 验证码的倒计时，防刷新

index_img: https://img-blog.csdnimg.cn/20191113122723223.gif
lazyload: true
categories:
- javascript
tags:
- js
- javascript



---














```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <div class="form-group">
        <div class="input-group">
          <input id="mobile" type="text" class="form-control" maxlength="11" placeholder="请输入手机号码">
          <button class="btn input-group-addon">获取验证码</button>
        </div>
      </div>
    <script>
        const getVerificationCodeBTN = document.querySelector('.input-group-addon');
        var timeNUM;
        var times;
        let time = localStorage.getItem("time");
        getVerificationCodeBTN.onclick = () => {
          const mobile = document.querySelector('#mobile').value;
          if (mobile !== '' && mobile.length == 11) {
           /* $.ajax({
              typt: 'POST',
              url: 'http://91fangwei.web.zrtec.net/',
              async: false,
              data: {
                mobile: mobile
              },
              dataType: 'json',
              error: (err) => {
                console.log(err);
              }
            });*/
            // 验证码倒计时
            localStorage.clear();
            if (time == null || time == undefined || time < 0) {
              timeNUM = 60;
            };
            timer();
          } else {
            alert('请检查手机号\n输入有效手机号才能获取验证码哦');
          }
        };
        if (time == null || time == undefined) {
          timeNUM = 60;
        } else {
          timeNUM = time;
          timer();
        }
        function timer() {
          getVerificationCodeBTN.style.pointerEvents = 'none';
          getVerificationCodeBTN.classList.add('disabled');
          times = setTimeout(timer, 1000)
          timeNUM--;
          getVerificationCodeBTN.innerText = timeNUM + '后再获取';
          localStorage.setItem("time", timeNUM)
          if (timeNUM < 1) {
            localStorage.clear();
            clearTimeout(times);
            getVerificationCodeBTN.innerHTML = "重新获取";
            getVerificationCodeBTN.style.pointerEvents = 'auto';
            getVerificationCodeBTN.classList.remove('disabled');
          }
        }
    </script>
</body>

</html>
```

![js 验证码的倒计时，防刷新](https://img-blog.csdnimg.cn/20191113122723223.gif)


但遗留个bug：刷新频率有多快倒计时就走多快，而且还有偶现现象，关了该页面，过了很久再打开该页面还在倒计时！


