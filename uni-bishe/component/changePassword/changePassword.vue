<template>
	<view class="changePassword">
		<view class="phone">
			<label>手机号：</label>
			<input class="inputA" type="text" value="" placeholder="请输入手机号"	 v-model="phone" @blur="phoneCode(phone)" />
		</view>
		<view class="code">
			<label>验证码：</label>
			<input class="inputA" type="text" value="" placeholder="请输入验证码"	 />
			<span class='sendcode' >发送验证码</span>
		</view>
		<view class="password">
			<label>密码：</label>
			<input class="inputA" type="password" value="" placeholder="请输入密码" />
		</view>
		<view class="btn-login" @click="change()">
			修改
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phone:""
			};
			
		},
		methods:{
			phoneCode(){
				
			}
		},
		created() {
			let self=this
			uni.getStorage({
				key:'user_phone',
				success:function(res){
					console.log('local',res.data)
					self.phone=res.data
				},
				fail() {
					uni.showToast({
						title:'请输入手机号',
						icon:'none'
					})
				}
			})
			
		}
	}
</script>

<style lang="scss">
.changePassword{
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
		   // margin-top: 20rpx;
		}
		label{
			 float: left;
			 width: 200rpx;
			 text-align: right;
			 margin-top: 10rpx
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
			width: 30%;
		}
		.sendcode{
			position: absolute;
			right: 20rpx;
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
