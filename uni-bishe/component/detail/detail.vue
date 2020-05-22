<template>
	<view class="">
		<view class="top-msg">
			
		</view>
		<view class="detail" v-for="item in foodlist" :key='item.id'>
			<view class="detail-item" v-for="item2 in item.foodlist" :key='item2.id'>
				<image :src="item2.img" mode=""></image>
				<p><span>{{ item2.msg }}</span><span>￥{{ item2.price }}元/份</span></p>
				<view class="buy">
					购买
				</view>
			</view>
		</view>
	</view>
	</view>
	
</template>

<script>
	export default {
		/* navigateTo跳转 */
		/* 进入页面则发起请求 one/two=>detail*/
		onLoad(option) {
			console.log('detail',option.id)
			uni.setStorage({
				key:'id',
				data:option.id,
				success(res) {
					console.log('success',res)
				}
			})	
			
		},
		data() {
			return {
				foodlist:[]
			};
		},
		created() {
			let id;
			let self=this
			uni.getStorage({
				key:'id',
				success: function (res) {
				    console.log('res.data',res.data);
					id=res.data
				}
			})
			uni.request({
				url:'http://localhost:10086/detail',
				data:{
					id:String(id)
				},
				success(res) {
					console.log('detail-data',res.data.data)
					self.foodlist=res.data.data
				}
			})
		}
		
	}
</script>

<style lang="scss">
.detail{
	width: 100%;
	
	.detail-item{
		width: 48%;
		height: 300rpx;
		float: left;
		border:1px solid #ccc;
		position: relative;
		margin: 5rpx;
		image{
			width: 100%;
			height: 100%;
		}
		p{
			position: absolute;
			top:20rpx;
			left: 50%;
			transform: translateX(-50%);
			span{
				display: inline-block;
				width: 350rpx;
				height: 50rpx;
				text-align: center;
				line-height: 50rpx;
			}
		}
		.buy{
			position: absolute;
			bottom: 0;
			width: 100rpx;
			height: 60rpx;
			border: 1px solid #ccc;
			left: 50%;
			transform: translateX(-50%);
			line-height: 60rpx;
			text-align: center;
			background-color: red;
			border: 10rpx;
		}
	}
}
</style>
