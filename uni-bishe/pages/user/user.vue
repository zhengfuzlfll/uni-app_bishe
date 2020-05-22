<template>
	<view class="user">
	  <view class="touxiang">
	    <image class="img" src="../../static/logo.png"></image>
		<!-- <view>{{ user ? `<text>${user}</text>`:`<text @click="toLogin()">点击登录/注册</text>` }}</view> -->
	    <!-- <text @click="toLogin()">{{user?user:'点击登录/注册'}}</text> -->
		<!-- <div>{{user}}</div> -->
		<!-- <text v-show="isok">{{user}}</text>
		<text v-show="!isok" @click="toLogin()">点击登录/注册</text> -->
		<text v-if="user">{{user}}</text>
		<text v-else='' @click="toLogin()">点击登录/注册</text>
	  </view>
	  <view class="list">
	    <view @click="tousermsg()">
	      <image class="img2" src="../../static/resources/user/user.png"></image>
	      <text>账户信息</text>
	      <image class="img3" src="../../static/resources/user/arrow.png"></image>
	    </view>
	    <view @click="touserorder()">
	      <image class="img2" src="../../static/resources/user/order.png"></image>
	      <text>我的订单</text>
	      <image class="img3" src="../../static/resources/user/arrow.png"></image>
	    </view>
	    <view @click="tousernotice()">
	      <image class="img2" src="../../static/resources/user/message.png"></image>
	      <text>系统通知</text>
	      <image class="img3" src="../../static/resources/user/arrow.png"></image>
	    </view> 
	  </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user:'',
				isok:false,
				text:'点击登录/注册'
			}
		},
		methods: {
			/* 登录/注册 */
			toLogin(){
				uni.navigateTo({
				    url: '../login/login'
				});
			},
			/* 个人信息 */
			tousermsg(){
				uni.navigateTo({
				    url: '../../component/usermsg/usermsg'
				});
			},
			/* 订单列表 */
			touserorder(){
				uni.navigateTo({
				    url: '../../component/userorder/userorder'
				});
			},
			tousernotice(){
				uni.navigateTo({
				    url: '../../component/usernotice/usernotice'
				});
			}
			
		},
		created() {
			let self=this
			uni.getStorage({
				key:'user_phone',
				success: function (res) {
				    console.log(res.data)
					if(res.data){
						self.user=res.data
						self.isok=false
					}
				}
			})
			
		}
	}
</script>

<style scoped lang="scss">
/* pages/user/user.wxss */
page{
  width: 100%;
  height: 100%;
}
.user{
  width: 100%;
  height: 100%;
  /* margin-top:10px; */
}
.user .touxiang{
  height: 100px;
  background: #efefef;
  /* line-height: 100px; */
  margin: auto;
}
.user .touxiang image{
    width:60px;
    height: 60px;
    padding: 20px 10px;
    border-radius: 50%;
    float: left;
}
.user .touxiang text{
  display: inline-block;
  height: 100px;
  line-height: 100px;
  float: left;
}
.user .list{
  width: 100%;
  height: 60px;
 
}
.user .list view{
  width: 100%;
  height: 60px;
padding-left: 10px;
  border-bottom: 1px solid #ccc;
  line-height: 60px;
  margin-bottom: 10px;
  /* background: rgb(177, 169, 166); */
  position: relative;
}
.user .list view image{
  width: 30px;
  height: 30px;
  padding: 5px;
  float: left;
  padding-top: 15px;
}
.user .list view text{
  float: left;
}
.user .list view .img3{
  position: absolute;
  right: 30px;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
}

</style>
