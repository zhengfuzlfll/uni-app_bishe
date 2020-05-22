<template>
	<view class="chatadd">
		<textarea value="" placeholder="请先登录,再使用" v-model="msg" />
		<view class="submit" @click="submit()">
			提交
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg:''
			};
		},
		methods:{
			submit(){
				console.log(this.msg)
				if(this.msg.trim()){
					let a=new Date().toLocaleString().split(' ')
					let date=a[0]//日期
					let time=a[1].slice(2,-3)//时间
					let self=this
					uni.getStorage({
						key:'user_phone',
						success(res) {
							if(!res.data){
								uni.showToast({
									title:'请先登录',
									icon:'none'
								})
							}else{
								// phone=res.data
								uni.request({
									url:'http://localhost:10086/chat/insert',
									method:'POST',
									data:{
										phone:res.data,
										msg:self.msg,
										date,
										time
									}
								}),
								uni.switchTab({
								    url: '../../pages/chat/chat'
								});
							}
							
						}
					})
					// console.log(time,now,phone)
				}else{
					uni.showToast({
						title:'请输入内容',
						icon:'none'
					})
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
.chatadd{
	textarea{
		border: 1rpx solid #ccc;
		width: 98%;
		margin:auto;
		min-height:300rpx;
		margin-top:10rpx ;
	}
	.submit{
		width: 100rpx;
		height: 80rpx;
		border:1rpx solid #ccc;
		float: right;
		margin-right:50rpx ;
		margin-top: 30rpx;
		text-align: center;
		line-height: 80rpx;
	}
}
</style>
