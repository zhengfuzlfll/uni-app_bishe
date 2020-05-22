<template>
	<view class="userorder">
		<ul class='list'>
			<li>
				<text class="food">米饭1+鱼香肉丝5+油麦菜1+米饭1+鱼香肉丝5+油麦菜1</text>
				<view class="msg">一食堂二楼午餐，2020-1-1</view>
				<text class="totalprice">￥6</text>
			</li><li>
				<text class="food">米饭1+鱼香肉丝5+油麦菜1+米饭1+鱼香肉丝5+油麦菜1</text>
				<view class="msg">一食堂二楼晚餐，2020-1-1</view>
				<text class="totalprice">￥6</text>
			</li><li>
				<text class="food">米饭1+鱼香肉丝5+油麦菜1+米饭1+鱼香肉丝5+油麦菜1</text>
				<view class="msg">一食堂二楼早餐，2020-1-1</view>
				<text class="totalprice">￥6</text>
			</li><li>
				<text class="food">米饭1+鱼香肉丝5+油麦菜1+米饭1+鱼香肉丝5+油麦菜1</text>
				<view class="msg">一食堂二楼早餐，2020-1-1</view>
				<text class="totalprice">￥6</text>
			</li>
			
		</ul>
		
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
ul,li{
	list-style: none;
}
.userorder{
	width: 100%;
	.list{
		padding: 0;
		width: 100%;
		li{
			// height: 100rpx;
			border-bottom: 1rpx solid #ccc;
			padding-left:10rpx ;
			position:relative;
			overflow: auto;
			width: 100%;
			
			.food{
				width: 70%;
				overflow: auto;
			}
			.msg{
				font-size: 12rpx;
			}
			.totalprice{
				position: absolute;
				right: 50rpx;
				top: 20rpx;
				display: block;
				width: 200rpx;
				height: 50rpx;
				background-color: #efefef;
				opacity: 0.8;
				text-align: center;
				line-height: 50rpx;
			}
		}
	}
}
</style>
