<template>
	<view class="chat">
		<image @click="chatadd()" class="add" src="../../static/resources/chat/tianjia.png" mode=""></image>
		<ul>
			<li v-for='item in chatlist' :key='item.id'>
				<view class="">
					{{item.msg}}
				</view>
				<view class="">
					<text>发表者：{{item.phone}}</text>
					<text>-{{item.date , item.time}}</text>
				</view>
			</li>
		</ul>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				chatlist:''
			}
		},
		methods: {
			/* 点击进入另外的页面 */
			chatadd(){
				uni.navigateTo({
				    url: '../../component/chatadd/chatadd'
				});
			}
		},
		created() {
			let self=this
			uni.request({
				url:'http://localhost:10086/chat',
				success(res) {
					
					self.chatlist=res.data.data.reverse()
					// console.log('chat',res.data.data.reverse())
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
