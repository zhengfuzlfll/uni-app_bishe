<template>
	<view class="one">
		<view class="left">
			<ul style='padding: 0;'>
				<li v-for="(item,index) in nav" :key="index" @click="selected(item.id)" :class="item.id===isSelected?'active':''">{{item.text}}</li>
			</ul>
		</view>
		<view class="right">
			<!-- 顶部 -->
			<view class="right_top">
				<ul>
					<li v-for='item2 in nav2' :key='item2.idx' @click="change(item2.idx)" :class="item2.idx===isSelected2?'cur':''">{{ item2.text2 }}</li>
				</ul>
			</view>
			<!-- 底部 -->
			<!-- <view class="food_list" > -->
			<view class="food_list" v-for="item in foodlist"  :key='item.id'> 
				<view class="list2" v-for="item2 in item.item" :key='item2.id' v-show="item2.flag==isSelected2" @click="toDetail(item2.id)">
					 	<image :src="item2.img" mode=""></image>
						<p>{{item2.flag==1?'一':'二'}}楼{{item2.msg}}号窗口</p>
				</view>
				
				<!-- <view class="list2">
					<image src="../../static/logo.png" mode=""></image>
					<p>一楼3号窗口</p>
				</view> -->
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
				nav2:[{idx:1,text2:'一楼'},{idx:2,text2:'二楼'}],
				"isSelected2":1,
				"foodlist":[]
			}
		},
		methods: {
			/* 左边 早餐、午餐、晚餐*/
			selected(id){
				/* 高亮 */
				this.isSelected=id
				// console.log(this.isSelected)
				/* 在request里无法使用this,解决办法：在request前将this存起来 */
				let self=this
				if(id==1){
					id=1
				}
				uni.request({
					url: 'http://localhost:10086/list',
					data:{
						id:String(id)
					},
					success(res) {
					console.log('res',res.data.data)
					self.foodlist=res.data.data
					// console.log('this',self)
					}
				})
			},
			/* 右边 一楼、二楼*/
			change(id){
				this.isSelected2=id
			},
			/* 跳转详情页  =>传参 */
			toDetail(id){
				console.log('id',id)
				uni.navigateTo({
					url:`../../component/detail/detail?id=${id}`
				})
			}
		},
		/* 页面首次加载进入请求数据 */
		created() {
			/* 坑 */
			/* 在request里无法使用this,解决办法：在request前将this存起来 */
			let self=this
			uni.request({
				 url:'http://localhost:10086/list',
				 data:{
					 id:'1'
				 },
				 success(res) {
				 	console.log('res-first',res.data.data[0])
					self.foodlist=res.data.data
					// console.log('this.foodlist',self.foodlist)
				 }
			})
		}
	
	}
</script>

<style lang="scss" scoped>
	ul,li{
		list-style: none;
	}
.one{
	display: flex;
	.left{
		width: 120rpx;
		position: fixed;
		ul{
			li{
				display: block;
				height: 150rpx;
				line-height: 150rpx;
				text-align: center;
				font-size: 40rpx;
				border-bottom: 1rpx solid #ccc;
				border-right:1rpx solid #ccc ;
				font-weight: 600;
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
		margin-left: 120rpx;
		.right_top{
			height: 100rpx;
			line-height: 100rpx;
			text-align: center;
			font-size: 40rpx;

			ul{
				display: flex;
				border-bottom: 1rpx solid #ccc ;
				/* 覆盖H5默认的左边padding的40px */
				padding: 0 !important;
				li{
					flex: 1;
					border-right: 1rpx solid #ccc;
					font-weight: 600;
				}
				.cur{
					background: red;
					color: white;
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
				image{
					width: 98%;
					height: 300rpx;
					float: left;
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
					background: red;
					color: white;
				}
			}
		}
	}
}
</style>
