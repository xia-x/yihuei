<template>
	<view class="login_con">
		<image src="../../static/img/login_logo.png"></image>
		<view class="login_info">
			<view class="login_type">
				<view :class="[logintype?'choice':'']" @click="changelogintype">快捷登录</view>
				<view :class="[logintype?'':'choice']"  @click="changelogintype">密码登录</view>
			</view>
			<view class="userinfo_con">
				<view>
					<input placeholder="请输入手机号"  @input="getphone"/>
				</view>
				<view v-show="logintype">
					<view><input placeholder="请输入验证码" @input="getphonecode"/></view>
					<button class="login_code">获取验证码</button>
				</view>
				<view v-show="!logintype">
					<input placeholder="请输入密码" @input="getpassword"/>
				</view>
			</view>
			<button class="login_btn" @click="userlogin">登录</button>
		</view>
		<view class="wx_login">新用户注册|微信登录</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logintype:true,
				phonecode:"",
				phone:"",
				password:"",
				
			}
		},
		methods: {
			changelogintype(){
				this.logintype = !this.logintype;
				console.log(this.logintype)
			},
			userlogin(){	
				var phonerg = RegExp(/^1[345798]\d{9}$/)
				console.log(this.phone)
				console.log(phonerg.test(this.phone))
				if(!phonerg.test(this.phone)){
					uni.showToast({
						title:"手机格式不正确",
						icon:"none"
					})
					return;
				}
				uni.setStorageSync("loginflag",true)
				uni.switchTab({
					url:"../myinfo/myinfo"
				})
			},
			getphone(e){
				this.phone =e.detail.value
				console.log(e.detail.value)
			},
			getphonecode(e){
				this.phonecode =e.detail.value
				console.log(e.detail.value)
			},
			getpassword(e){
				this.password =e.detail.value
				console.log(e.detail.value)
			},
			checkMobile(value){
				return RegExp(/^1[345798]\d{9}$/).test(value);
			}
		}
	}
</script>

<style lang="scss" scoped>
	.login_con{
		margin: 85rpx 100rpx;
		text-align: center;
		color: $font-color-b;
		font-size: 26rpx;
		image{
			width: 160rpx;
			height: 170rpx;
		}
		.login_info{
			text-align:left;
			.choice{
				color: $font-color-a;
				border-bottom: 4rpx solid $font-color-a;
				padding-bottom: 10rpx;
			}
			.login_type{
				display: flex;
				view{
					width:110rpx;
					margin: 26rpx 26rpx 26rpx 0rpx;
				}
			}
			.userinfo_con{
				margin: 32rpx 0rpx;
				view{
					margin: 14rpx 0rpx;
					padding: 26rpx 0rpx;
					border-bottom:1rpx solid $font-color-b ;
				} 
				.login_code{
					margin: 25rpx 0rpx 16rpx 10rpx; 
					padding: 10rpx 30rpx;
					height: 90rpx;
					width: 230rpx;
					line-height:80rpx ;
					font-size:26rpx;
				}
				view:nth-child(2){
					padding: 0rpx;
					margin: 0rpx;
					display: flex;
					width: 100%;
					justify-content: space-between;
					border: none;
					view{
					 border-bottom:1rpx solid $font-color-b ;	
					}
				}
			  }
			  .login_btn{
				  background: $font-color-c;
				  color: #fff;
			  }
			}
			.wx_login{
				position: fixed;
				bottom: 100rpx;
				width: 70%;
			}
		}
</style>
