<template>
	<view class="home">
		<!-- 轮播图 -->
		<view class="show">
			<view class="notice-icon">
				<image src="../../static/resources/home/热卖.png" mode=""></image>
				<text>推荐菜式</text>
			</view>
			<swiper indicator-dots autoplay interval="3000" circular class="home-top">
				<swiper-item>
					<image src="http://img1.imgtn.bdimg.com/it/u=1803174689,3504160992&fm=26&gp=0.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image src="http://img3.imgtn.bdimg.com/it/u=1719390190,2644315671&fm=26&gp=0.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image src="http://img5.imgtn.bdimg.com/it/u=3693979980,3454780521&fm=26&gp=0.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image src="http://img3.imgtn.bdimg.com/it/u=1046980313,343520860&fm=26&gp=0.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image src="http://img0.imgtn.bdimg.com/it/u=3449663486,3264178046&fm=26&gp=0.jpg"></image>
				</swiper-item>
			</swiper>
		</view>
		
		
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
			<view class="notice-icon">
				<image src="../../static/resources/home/失物招领.png" mode=""></image>
				<text>失物招领</text>
			</view>
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item>
					<view class="swiper-item">
						急寻：由于不慎丢失金士顿银色U盘一枚，内含重要数据，
						望拾到者归还，好人有好报，本人联系方式QQ：111111
					</view>
				</swiper-item>
				<!-- <swiper-item>
					<view class="swiper-item">2</view>
				</swiper-item> -->
			</swiper>
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
	image{
		width: 100%	;
		height: 100%;
	}
	.show,.notice,.lostandfound{
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
