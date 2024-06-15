---
title: uniapp 手机端时禁止输入框弹出键盘，使用自定义键盘

index_img: https://img-blog.csdnimg.cn/20191210165554465.png
lazyload: true
categories:
- uniapp


tags:
- uniapp
- 微信小程序


---




前言：我是用[uniapp](https://uniapp.dcloud.io/component/README)写的，有些地方有使用uniapp语法。

![vue 手机端时禁止输入框弹出键盘，使用自定义键盘](https://img-blog.csdnimg.cn/20191210165554465.png)
源码：
```html
<template>
	<view>
		<view class="captch">
			<view class="title-h1">短信验证码</view>
			<view class="title-h2">
				<view>已向您尾号 {{ tail }} 的手机发送验证码</view>
				<view class="count-down">
					<text>{{ seconds }} 秒后重新发送验证码</text>
					<button v-show="isSend" class="send-btn" @tap="getVerifyCode">获取验证码</button>
				</view>
			</view>
			<!-- 验证码输入框 -->
			<view class="inputing">
				<input v-model="num1" class="auth-code" maxlength="1" @focus="noKeybord" />
				<input v-model="num2" class="auth-code" maxlength="1" @focus="noKeybord" />
				<input v-model="num3" class="auth-code" maxlength="1" @focus="noKeybord" />
				<input v-model="num4" class="auth-code" maxlength="1" @focus="noKeybord" />
				<input v-model="num5" class="auth-code" maxlength="1" @focus="noKeybord" />
				<input v-model="num6" class="auth-code" maxlength="1" @focus="noKeybord" />
			</view>
			<view class="wrap"><button size="large" class="btn" @tap="onLogin">登录</button></view>
			<!-- 数字键 -->
			<view class="keyboard">
				<view class="key" v-for="(number, index) in 9" :key="index">
					<view class="btn" @tap="inputing(index + 1)">{{ index + 1 }}</view>
				</view>
				<view class="key"><view class="btn" @tap="a" style="visibility: hidden;">#</view></view>
				<view class="key"><view class="btn" @tap="inputing(0)">0</view></view>
				<view class="key"><view class="btn" @tap="delet">×</view></view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			seconds: 180,
			isSend: false,
			showModal: false,
			num1: '',
			num2: '',
			num3: '',
			num4: '',
			num5: '',
			num6: '',
			tail: '1111',
			phone: ''
		};
	},
	onLoad(option) {
		this.countDown();  // 开始倒数计时
		this.phone = option.phone;
		// this.tail = ;
	},
	onUnload() {
		clearInterval(timers); // 删除定时器
		uni.removeStorageSync('count_down'); // 移除缓存里的定时器
	},
	methods: {
		countDown() {
			uni.setStorageSync('count_down', this.seconds);
			var timers = setInterval(() => {
				this.seconds--;
				// console.log(this.seconds);
				uni.setStorageSync('count_down', this.seconds);
				if (this.seconds === 0) {
					this.isSend = true;
					clearInterval(timers);
					this.seconds = 180;
					uni.setStorageSync('count_down', this.seconds);
				}
			}, 1000);
		},
		noKeybord() {
			//document.activeElement.blur(); // 禁止输入框对焦（禁止弹出原生键盘）
			uni.hideKeyboard();
		},
		// 数字键盘
		inputing(num) {
			if (this.num1.length == '') {
				this.num1 = num;
			} else if (this.num2.length == '') {
				this.num2 = num;
			} else if (this.num3.length == '') {
				this.num3 = num;
			} else if (this.num4.length == '') {
				this.num4 = num;
			} else if (this.num5.length == '') {
				this.num5 = num;
			} else if (this.num6.length == '') {
				this.num6 = num;
			} else {
				uni.showToast({
					title: '输入已够6位！',
					icon: 'none'
				});
			}
		},
		// 删除键
		delet() {
			if (this.num6.length == 1 && this.num5.length == 1 && this.num4.length == 1 && this.num3.length == 1 && this.num2.length == 1 && this.num1.length == 1) {
				this.num6 = '';
			} else if (this.num5.length == 1 && this.num4.length == 1 && this.num3.length == 1 && this.num2.length == 1 && this.num1.length == 1) {
				this.num5 = '';
			} else if (this.num4.length == 1 && this.num3.length == 1 && this.num2.length == 1 && this.num1.length == 1) {
				this.num4 = '';
			} else if (this.num3.length == 1 && this.num2.length == 1 && this.num1.length == 1) {
				this.num3 = '';
			} else if (this.num2.length == 1 && this.num1.length == 1) {
				this.num2 = '';
			} else if (this.num1.length == 1) {
				this.num1 = '';
			}
		},
		//重新获取验证码
		getVerifyCode() {
			this.isSend = false;
			this.countDown();
			uni.showToast({
				title: '已发送验证码',
				icon: 'none'
			});
		},
		// 登录
		onLogin() {
			let params = this.num1 + this.num2 + this.num3 + this.num4 + this.num5 + this.num6;
			if(params.length<6){
				uni.showToast({
					title: '验证码不足6位！',
					icon: 'none'
				});
			}else{
				console.log(params);
			}
		}
	}
};
</script>

<style lang="scss" scoped>
uni-page-body {
	background-color: #76d767;
}

.captch {
	height: 100%;
	background-color: #76d767;
	background-image: url(/static/login-bj.png);
	background-position: 100% 100%;
	background-size: cover;
	padding: 54rpx;

	.title-h1 {
		font-size: 28rpx;
		line-height: 50rpx;
		color: #ffffff;
		width: 100%;
		text-align: center;
		margin-top: 12%;
		font-weight: 600;
		letter-spacing: 1px;
	}

	.title-h2 {
		font-size: 24rpx;
		color: #ffffff;
		width: 480rpx;
		text-align: left;
		font-weight: 400;
		line-height: 40rpx;
		margin: 40rpx auto 0;
	}

	.count-down {
	}

	.send-btn {
		width: 160rpx;
		height: 44rpx;
		background: #ffffff;
		box-shadow: 1px 1px 1px 0px #3ebe2a;
		border-radius: 22rpx;
		font-size: 20rpx;
		height: 40rpx;
		line-height: 40rpx;
		font-weight: 400;
		color: #3ebe2a;
		display: inline-block;
		transform: translateY(4rpx);
		float: right;
	}

	.inputing {
		margin: 60rpx 0 80rpx;
		color: #ffffff;
		font-size: 32rpx;
		display: flex;
		justify-content: space-between;

		.auth-code {
			font-weight: 600;
			border-bottom: 1px solid #f1f1f1;
			margin: 0px 16rpx;
			text-align: center;
			padding-bottom: 17rpx;
			height: 80rpx;
		}
	}

	.keyboard {
		margin-top: 60rpx;
		padding-bottom: 60rpx;
		display: grid;
		grid-template-columns: 25% 25% 25%;
		grid-auto-rows: 25% 25% 25% 25%;
		justify-content: space-between;

		.key {
			text-align: center;
			color: white;
			margin-bottom: 50rpx;

			.btn {
				border-bottom: 1px solid white;
				padding-bottom: 18rpx;
				font-size: 40rpx;
				font-weight: 500;
			}
		}
	}

	.wrap {
		margin-top: 40px;

		.btn {
			background: #3ebe2a;
			color: #ffffff;
			font-size: 32rpx;
		}

		uni-button:after {
			border: none;
		}
	}
}
</style>
```

![vue 手机端时禁止输入框弹出键盘，使用自定义键盘](https://img-blog.csdnimg.cn/20191210165741688.gif)

重点部分：
![vue 手机端时禁止输入框弹出键盘，使用自定义键盘](https://img-blog.csdnimg.cn/20200312145503994.png)

![vue 手机端时禁止输入框弹出键盘，使用自定义键盘](https://img-blog.csdnimg.cn/20200124134850572.png)




