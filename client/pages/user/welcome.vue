<template>
	<view class="welcome">
		<navigator url="./login" hover-class="none">
			<button type="primary" class="blue">登录</button>
		</navigator>
		<navigator url="./register" hover-class="none">
			<button type="default" class="success">新用户</button>
		</navigator>
	</view>
</template>

<script>
export default {
	data() {
		return {
			
		};
	},
	onLoad() {},
	methods: {}
};
</script>

 <style scoped lang="scss" type="text/css">
.welcome{
  position:absolute;
  width:100%;
  height:100%;
  background: url('~@/static/images/splash.png') no-repeat center center;
  background-size: contain;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  button{
	 margin:0 0 150rpx 50rpx;
	 width: 200rpx;
  }
}
</style>
