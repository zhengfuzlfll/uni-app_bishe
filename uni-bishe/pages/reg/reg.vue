<template>
	<view class="login">
		<navigator url="../login/login">
			<view class="toLogin">
				<p class='button'>登录</p>
			</view>
		</navigator>
		<view class="phone">
			<label>手机号：</label>
			<input class="inputA" type="text" value="" placeholder="请输入手机号" v-model="phonemsg" @blur="phone(phonemsg)" />
		</view>
		<view class="code">
			<label>验证码：</label>
			<input class="inputA" type="text" value="" placeholder="验证码" v-model="codemsg" @blur="code(codemsg)"/>
			<span class='sendcode'>发送验证码</span>
		</view>
		<view class="password">
			<label>密码：</label>
			<input class="inputA" type="text" value="" placeholder="请输入密码" v-model='passwordmsg' @blur="password(passwordmsg)"/>
		</view>
		<view class="password2">
			<label>确认密码：</label>
			<input class="inputA" type="text" value="" placeholder="确认密码" v-model="passwordmsg2" @blur="password2(passwordmsg2)"/>
		</view>
		<view class="btn-login" @click="reg()">
			注册
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phonemsg:'',
				codemsg:'',
				passwordmsg:'',
				passwordmsg2:'',
				isok:false,
				istrue:false,
				isright:false
			}
		},
		methods: {
			/* 手机号 */
			phone(value){
				let phoneReg=/^1[3-9]\d{9}$/; 
				let self=this
				if(value.trim().length){
					if(phoneReg.test(value)){
						uni.request({
							url:'http://localhost:10086/user',
							data:{
								phone:value
							},
							success(res) {
								console.log(res.data.code)
								if(res.data.code){
									uni.showToast({
										title:'该账号已注册',
										icon:'none'
									})
								}else{
									// uni.showToast({
									// 	title:'请发送验证码',
									// 	icon:'none'
									// })
									/* 可以注册 */
									self.isok=true
								}
							}
						})
					}else{
						uni.showToast({
								title:'手机号不正确',
								icon:'none'
							})
					}
				}else{
					uni.showToast({
						title:'手机号不能为空',
						icon:'none'
					})
				}
			},
			/* 验证码 */
			code(value){
				console.log(value)
				let codeReg=/^[0-9]{6}$/
				if(value.trim().length){
					if(codeReg.test(value.trim())){
						uni.showToast({
							title:"验证通过",
							icon:'none'
						})
					}else{
						uni.showToast({
							title:"验证码不合法",
							icon:'none'
						})
					}
				}else{
					uni.showToast({
						title:"验证码不能为空",
						icon:'none'
					})
				}
			},
			password(value){
				console.log(value)
				let passwordReg=/^[1-9a-zA-Z]{6,20}$/
				let self=this
				if(value.trim().length){
					if(passwordReg.test(value.trim())){
						/* 密码验证通过 */
						self.istrue=true
					}else{
						uni.showToast({
							title:'密码格式不正确',
							icon:'none'
						})
					}
				}else{
					uni.showToast({
						title:'密码不能为空',
						icon:'none'
					})
				}
			},
			password2(value){
				console.log(value)
				if(this.passwordmsg===value){
					this.isright=true
				}else{
					uni.showToast({
						title:'两次密码不一致',
						icon:'none'
					})
				}
			},
			reg(){
				console.log(22222)
				let self=this
				if(this.phonemsg.length && this.passwordmsg.length && this.passwordmsg2.length && this.codemsg.length){
					if(this.isok && this.istrue && this.isright){
						uni.setStorage({
							key:'phone',
							value:this.phonemsg.trim()
						}),
						uni.request({
							url:'http://localhost:10086/user/reg',
							method:'POST',
							data: {
							        phone: 'name',
							        password: '18'
							    },
						}),
						uni.reLaunch({
							url:'../login/login'
						})
					}else{
						uni.showToast({
							title:'手机号或密码不正确',
							icon:'none'
						})
					}
				}else{
					uni.showToast({
						title:'请完整填写信息',
						icon:'none'
					})
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
.login{
	width: 98%;
	// background: yellow;
	margin:auto;
	view{
		width: 100%;
		margin-top: 20px;
		input{
		   width: 50%; 
		   height: 80rpx;
		   border: 1px solid black;
		   padding-left: 10rpx;
		  
		}
		label{
			 float: left;
			 width: 200rpx;
			 text-align: right;
		}
	}
	.btn-login{
		width: 300rpx;
		height: 100rpx;
		border: 2rpx solid red;
		text-align: center;
		line-height: 100rpx;
		margin: auto;
		margin-top: 20rpx;
		background-color:red;
		color: white;
	}
	.phone{
		margin: 0;
		padding-top:20rpx ;	
	}
	.code{
		position: relative;
		input{
			width: 40%;
		}
		.sendcode{
			position: absolute;
			right: 10rpx;
			top: 50%;
			transform: translateY(-50%);
			color: blue;
		}
	}
	.toLogin{
			height: 50rpx;
			position: relative;
			// margin-bottom: 50rpx;
			margin: 0;
			.button{
				width: 100rpx;
				height: 60rpx;
				position: absolute;
				right:30rpx ;
				top:50%;
				border:1px solid black;
				line-height: 60rpx;
				text-align: center;
			}
		}
}
</style>
