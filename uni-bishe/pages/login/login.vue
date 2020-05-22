<template>
	<view class="login">
			
		<navigator url="../reg/reg">
			<view class="toReg">
				<p class='button'>注册</p>
			</view>
		</navigator>
		
		<view class="phone">
			<label>手机号：</label>
			<input class="inputA" type="text" v-model="phonemsg" value="" placeholder="请输入手机号" @blur="phone(phonemsg)" />
		</view>
		<view class="password">
			<label>密码：</label>
			<input class="inputA" type="password" value="" placeholder="请输入密码" v-model="passwordmsg" @blur="password(passwordmsg)"/>
		</view>
		<view class="btn-login" @click="login()">
			登录
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phonemsg:'',
				passwordmsg:'',
				isok:false,
				istrue:false
			}
		},
		methods: {
			/* 输入的手机号是否正确 */
			// let phoneReg=/^1[3-9]\d{9}$/;
			// let passwordReg=/^[1-9a-zA-Z]{6,20}$/;
			// let isok=false;
   //          let istrue=false;
			phone(value){
				console.log(value)
				let self=this
				let phoneReg=/^1[3-9]\d{9}$/;
				if(value.trim().length){
					if(phoneReg.test(value.trim())){
					uni.request({
						url:'http://localhost:10086/user',
						data:{
							phone:value
						},
						success(res) {
							console.log(res.data.code)
							if(res.data.code){
								uni.showToast({
									title:'校验通过',
									icon:'none',
									duration:3000
								})
								self.isok=true
							}else{
								uni.showToast({
									title:'该账号未注册，请先注册',
									icon:'none',
									duration:3000
								})
							}
						}
					})
					}
				}else{
					uni.showToast({
						title:'手机号不能为空',
						icon:'none',
						duration:3000
					})
				}
			},
			password(value){
				let self=this
				console.log(value)
				let passwordReg=/^[1-9a-zA-Z]{6,20}$/
				if(value.trim().length){
					if(passwordReg.test(value)){
						uni.request({
							url:'http://localhost:10086/user',
							data:{
								phone:self.phonemsg,
								password:self.passwordmsg
							},
							success(res) {
								console.log('密码',res)
								if(res.data.code){
									// uni.showToast({
									// 	title:'验证通过',
									// 	icon:'none'
									// }),
									self.istrue=true
								}else{
									uni.showToast({
										title:'验证不通过',
										icon:'none'
									})
								}
							}
						})
					}else{
						uni.showToast({
							title:'密码不符合规范',
							icon:'none'
						})
					}
				}else{
					uni.showToast({
						title:'密码不能为空',
						icon:'none',
						duration:3000
					})
				}
			},
			login(){
				if(this.phonemsg.length&&this.passwordmsg.length){
					if(this.isok&&this.istrue){
						uni.reLaunch({
							url:'../home/home'
						}),
						uni.setStorage({
							key:'user_phone',
							data:this.phonemsg
						})
					}else{
						uni.showToast({
							title:'账号或密码错误',
							icon:'none'
						})
					}
				}else{
					uni.showToast({
						title:'请输入账号密码',
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
	.toReg{
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
