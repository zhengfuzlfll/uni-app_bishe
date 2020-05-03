<template>
	<view class="user">
	  <view class="touxiang">
	    <image class="img" src="../../static/logo.png"></image>
	    <text>昵称</text>
	  </view>
	  <view class="list">
	    <view>
	      <image class="img2" src="../../static/resources/user/user.png"></image>
	      <text>账户信息</text>
	      <image class="img3" src="../../static/resources/user/arrow.png"></image>
	    </view>
	    <view>
	      <image class="img2" src="../../static/resources/user/order.png"></image>
	      <text>我的订单</text>
	      <image class="img3" src="../../static/resources/user/arrow.png"></image>
	    </view>
	    <view>
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
				
			}
		},
		methods: {
			
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
