<script>
	import Vue from 'vue'
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
			let phone
			uni.getStorage({
				key:'user_phone',
				success:function(res){
					console.log(res.data)
					phone=res.data
				}
			})
			if(!phone){
				uni.reLaunch({
					url:'./pages/login/login'
				})
			}
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
