<template>
	<view class="detailall">
		<view class="top-msg">
			<view class="">
				一食堂一楼一号窗口
			</view>
			<image src="../../static/resources/one/购物车.png" mode="" @click="shopcar()"></image>
		</view>
		<!-- 展示菜品 -->
		<view class="detail" v-for="item in foodlist" :key='item.id'>
			<view class="detail-item" v-for="item2 in item.foodlist" :key='item2.id'>
				<image :src="item2.img" mode=""></image>
				<p><span>{{ item2.msg }}</span><span>￥{{ item2.price }}元/份</span></p>
				<view class="buy" @click="buy(item2.id)">
					添加
				</view>
			</view>
		</view>
		<!-- 是否显示已选购商品 -->
		<view class="hasorder" v-show="isshow">
			<ul>
				<li><text class="left">米饭</text><text class="right">￥5.00</text></li>
				<li><text class="left">米饭</text><text class="right">￥5.00</text></li>
				<li><text class="left">米饭</text><text class="right">￥5.00</text></li>
				<li><text class="left">米饭</text><text class="right">￥5.00</text></li>
				<li><text class="left">米饭</text><text class="right">￥5.00</text></li>
			</ul>
			<view class="total">
				总价：￥25
			</view>
			<view class="button">
				<text class="buy-btn">购买</text>
				<text class="add-btn" @click="addbtn()">继续添加</text>
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
				foodlist:[],
				flag:true,
				isshow:false
			};
		},
		methods:{
			/* 购买 */
			buy(id){
				console.log(id)
				// this.flag=false
				
			},
			shopcar(){
				this.isshow=!this.isshow
			},
			addbtn(){
				this.isshow=!this.isshow
			}
		}
		,
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
ul,li{
	list-style: none;
	padding: 0;
}
.detailall{
	.top-msg{
		width: 98%;
		background: #ccc;
		margin: auto;
		height: 100rpx;
		line-height: 100rpx;
		position: relative;
		image{
			width: 80rpx;
			height: 80rpx;
			// float: right;
			position: absolute;
			right: 0;
			top: 50%;
			transform: translateY(-50%);
		}
		// text{
		// 	float: left;
		// }
	}
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
				bottom: 10rpx;
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
	.hasorder{
		width: 100%;
		height: 100%;
		position: absolute;
		left: 0;
		top: 100rpx;
		background: white;
		// position: relative;
		.button{
			width: 100%;
			height: 98rpx;
			text-align: center;
			margin-top: 20rpx;
			text{
				width: 200rpx;
				height: 98rpx;
				display: inline-block;
				line-height: 98rpx;
				text-align: center;
				margin: auto;
				border: 1rpx solid red;
				// color: white;
				background: #efefef;
			}
			.buy-btn{
				background: red;
			}
			.add-btn{
				border-color: #efefef;
			}
		}
		ul{
			
			li{
				height: 80rpx;
				line-height: 80rpx;
				border-bottom: 1rpx solid #ccc;
				// width: 90%;
				margin: auto;
				padding-left:20rpx ;
				padding-right:20rpx;
				.left{
					float: left;
				}
				.right{
					float: right;
				}
			}
		}
	}
}

</style>
