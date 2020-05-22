<template>
	<view class="chatadd">
		<textarea value="" placeholder="请输入文字" />
		<view class="submit">
			提交
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
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
