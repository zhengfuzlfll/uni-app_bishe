<template>
	<view class="chat">
		<image @click="chatadd()" class="add" src="../../static/resources/chat/tianjia.png" mode=""></image>
		<ul>
			<li>
				<view class="">
					【问题】食堂路口的灯坏了，希望修理或更换一下
				</view>
				<view class="">
					<text>发表者：XX</text>&nbsp;&nbsp;&nbsp;&nbsp;
					<text>2020-10-9 09:36</text>
				</view>
			</li>
		</ul>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			chatadd(){
				uni.navigateTo({
				    url: '../../component/chatadd/chatadd'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	ul,li{
		list-style: none;
		padding: 0;
	}
.chat{
	.add{
		width: 80rpx;
		height: 80rpx;
		position: fixed;
		right: 20rpx;
		top: 50%;
		transform: translateY(-50%);
	}
	ul{
		li{
			border-bottom: 1rpx solid #ccc;
			padding: 10rpx;
		}
	}
}
</style>
