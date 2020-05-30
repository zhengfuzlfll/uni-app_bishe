<template>
	<view class="usermsg">
		<ul class='msg'>
			<li>
				手机号：{{phone}}
			</li>
			<li class='li2' @click='changePassowrd()'>
				修改密码
				 <image class="img3" src="../../static/resources/user/arrow.png"></image>
			</li>
			
		</ul>
		<view class="logout" >
			<p @click="logout()">退出登录</p>
		</view>
		<view class="mask" v-show="isshow">
			<span class='surelogout'>确定退出？</span>
			<p>
				<span class='sure' @click='sureout()'>确定</span>
				<span @click='cancel()'>取消</span>
			</p>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phone:'',
				isshow:false
			};
		},
		methods:{
			/* 退出登录 */
			logout(){
				let self = this
				uni.getStorage({
					key:'user_phone',
					success(res) {
						console.log('res.data',res.data)
						// if(res.data){
							self.isshow=true
						// }else{
						// 	uni.showToast({
						// 		title:'您还没登录哦！',
						// 		icon:'none'
						// 	})
						// }
					},
					fail() {
						uni.showToast({
							title:'您还没登录哦！',
							icon:'none'
						})
					}
				})
				// this.isshow=true
			},
			/* 取消 退出*/
			cancel(){
				this.isshow=false
			},
			/* 确定退出 */
			sureout(){
				uni.removeStorage({
					key:'user_phone',
					success(res) {
						uni.redirectTo({
							url:'../../pages/login/login'
						})
							
						
					}
				})
			},
			/* 修改密码 */
			changePassowrd(){
				// console.log(666)
				uni.navigateTo({
					url:'../changePassword/changePassword'
				})
			}
		},
		created() {
			/* 获取用户手机号 */
			let self=this
			uni.getStorage({
				key:'user_phone',
				success(res) {
					self.phone=res.data
				}
			})
		}
	}
</script>

<style lang="scss" scoped>
	ul,li{
		list-style: none;
		padding: 0;
	}
	
	.usermsg{
		width: 95%;
		height: 100%;
		// background: yellow;
		margin: auto;
		position: relative;
		// padding-left:10rpx ;
		// padding-right: 10rpx ;
		.msg{
			// background-color: red;
			li{
				height: 100rpx;
				line-height: 100rpx;
				border-bottom: 1rpx solid #ccc;
			}
			.li2{
				position: relative;
				image{
					position: absolute;
					right: 30px;
					top: 50%;
					transform: translateY(-50%);
					width: 20px;
					height: 20px;
				}
			}
		}
		.logout{
			height: 200rpx;
			position: relative;
			p{
				width: 400rpx;
				height: 100rpx;
				background: orange;
				color: white;
				text-align: center;
				line-height: 100rpx;
				margin: auto;
				position: absolute;
				left: 50%;
				top: 50%;
				transform: translate(-50% ,-50%);
			}
		}
		.mask{
			width: 100%;
			height: 400rpx;
			background-color: black;
			opacity: 0.8;
			position: absolute;
			left: 0;
			top: 0;
			color: white;
			p{
				height: 80rpx;
				width: 410rpx;
				position: absolute;
				left: 50%;
				top: 50%;
				transform: translate(-50%,-50%);
				margin: auto;
				span{
					display: inline-block;
					width: 200rpx;
					height:80rpx;
					text-align: center;
					line-height: 80rpx;
					float: left;
					border: 1rpx solid red;
				}
				.sure{
					background-color: red;
					color: white;
				}
			}
			.surelogout{
				width: 100%;
				display:inline-block;
				text-align: center;
				margin-top: 100rpx;
			}
		}
	}
</style>
