<template>
	<view class="one">
		<view class="left">
			<list>
				<cell v-for="(item,index) in nav" :key="index" @click="selected(item.id)" :class="item.id===isSelected?'active':''">{{item.text}}</cell>
			</list>
		</view>
		<view class="right">
			<!-- 顶部 -->
			<view class="right_top">
				<list>
					<cell>一楼</cell>
					<cell>二楼</cell>
				</list>
			</view>
			<!-- 底部 -->
			<view class="food_list">
				<view class="list2">
					<image src="../../static/resources/home.png" mode=""></image>
					<p>一楼1号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼2号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view>
				<view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:'One',
		data() {
			return {
				nav:[{id:1,text:"早餐"},{id:2,text:"午餐"},{id:3,text:"晚餐"}],
				"isSelected":1,
				nav2:[{id:1,text:'一楼'},{id:2,text:'二楼'}]
			}
		},
		methods: {
			selected(id){
				// console.log(666)
				// console.log(id)
				this.isSelected=id
			}
		}
	}
</script>

<style lang="scss" scoped>
.one{
	display: flex;
	.left{
		width: 120rpx;
		// background: #007AFF;
		// float: left;
		position: fixed;
		list{
			// border-right: 1rpx solid #ccc;
			cell{
				display: block;
				height: 150rpx;
				line-height: 150rpx;
				text-align: center;
				font-size: 40rpx;
				border-bottom: 1rpx solid #ccc;
				border-right:1rpx solid #ccc ;
			}
			.active{
				background: red;
				color: white;
			}
		}
		
	}
	.right{
		
		width: 100%;
		flex: 1;
		// float: left;
		// display: flex;
		// flex-direction: column;
		margin-left: 120rpx;
		.right_top{
			height: 100rpx;
			line-height: 100rpx;
			text-align: center;
			font-size: 40rpx;
			// position: fixed;
			// left:120rpx;
			// top: 0;
			list{
				display: flex;
				border-bottom: 1rpx solid #ccc ;
				cell{
					flex: 1;
					border-right: 1rpx solid #ccc;
				}
			}
		}
		.food_list{
			margin-top: 10rpx;
			// flex: 1;
			overflow: auto;
			width: 100%;
			.list2{
				position: relative;
				width: 50%;
				float: left;
				// background: yellow;
				image{
					width: 98%;
					height: 300rpx;
					float: left;
					// margin-left: 8rpx;
					margin-bottom: 10rpx;
				}
				p{
					width: 98%;
					text-align: center;
					height: 50rpx;
					line-height: 50rpx;
					position: absolute;
					left: 50%;
					bottom: 10rpx;
					transform: translateX(-50%);
					// margin-left: 8rpx;
					background: red;
					color: white;
				}
			}
		}
	}
}
</style>
