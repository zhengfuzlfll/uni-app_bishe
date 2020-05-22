<template>
	<view class="home">
		<!-- 轮播图 -->
		<swiper indicator-dots autoplay interval="2000" circular class="home-top">
			<swiper-item>
			    <image src="../../static/logo.png"></image>
			</swiper-item>
			<swiper-item>
			    <image src="../../static/logo.png"></image>
			</swiper-item>
			<swiper-item>
			    <image src="../../static/logo.png"></image>
			</swiper-item>
			<swiper-item>
			    <image src="../../static/logo.png"></image>
			</swiper-item>
			<swiper-item>
			    <image src="../../static/logo.png"></image>
			</swiper-item>
		</swiper>
		
		<!-- 公告区 -->
		<view class="notice">
			<view class="notice-icon">
				<image src="../../static/resources/home/通知.png" mode=""></image>
				<text>公告栏</text>
			</view>
			<swiper indicator-dots autoplay interval="5000" circular>
				<swiper-item>
				    <view class="tongzhi"  style="padding: 10rpx;">
				    	通知：明天放假项目 'uni-bishe' 编译成功。前端运行日志，请另行在小程序开发工具的控制台查看。
				    </view>
					<view class="name" style="text-align: right;padding-right:20rpx;">
						校团委 
					</view>
					<view class="name" style="text-align: right;padding-right:20rpx;">
						2020-11-10
					</view>
				</swiper-item>
				<swiper-item>
				    <view class="tongzhi"  style="padding: 10rpx;">
				    	通知：食堂于明天（5.20）正常开放，欢迎广大师生就餐！
				    </view>
				    <view class="name" style="text-align: right;padding-right:20rpx;">
				    	食堂管理处 
				    </view>
				    <view class="name" style="text-align: right;padding-right:20rpx;">
				    	2020-05-19
				    </view>
				</swiper-item>
				<swiper-item>
				    <view class="tongzhi"  style="padding: 10rpx;">
				    	通知：各位同学请注意网络文明用语，共创文明网络环境各位
						同学请注意网络文明用语，共创文明网络环境
						各位同学请注意网络文明用语，共创文明网络环境
						各位同学请注意网络文明用语，共创文明网络环境
						各位同学请注意网络文明用语，共创文明网络环境通
						各位同学请注意网络文明用语，共创文明网络环境
						各位同学请注意网络文明用语，共创文明网络环境通
						各位同学请注意网络文明用语，共创文明网络环境通知
						：各位同学请注意网络文明用语，共创文明网络环境通知
						：各位同学请注意网络文明用语，共创文明网络环境通知：
						各位同学请注意网络文明用语，共创文明网络环境
				    </view>
				    <view class="name" style="text-align: right;padding-right:20rpx;">
				    	学生会 
				    </view>
				    <view class="name" style="text-align: right;padding-right:20rpx;">
				    	2020-5-21
				    </view>
				</swiper-item>
			</swiper>
		</view>
		
		<!-- 失物招领 -->
		<view class="lostandfound">
			<view >
				失物招领栏
			</view>
			<ul>
				<li>11</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default {
		name:"Home",
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
ul,li{
	list-style: none;
	padding: 0;
}
.home{
	.notice,.lostandfound{
		border-top: 1rpx solid #ccc;
		margin-top:10rpx ;
	}
	.notice{
		.notice-icon{
			height: 80rpx;
			line-height: 80rpx;
			background: #efefef;
			image{
				width: 50rpx;
				height: 50rpx;
				// display: inline-block;
				float: left;
				margin-top: 15rpx;
			}
			text{
				float: left;
				margin-left:10rpx ;
			}
		}
		swiper-item{
			overflow: auto;
		}
	}
}
</style>
