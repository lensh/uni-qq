<template>
	<uni-nav-bar :title="title" :fixed="true" color="white" statusBar backgroundColor="#47BAFE" :border="false" @clickLeft="showSideBar">
		<image src="/static/images/face.jpg" class="rounded-circle ml-2" style="width: 70rpx;height: 70rpx;" slot="left"></image>
	</uni-nav-bar>
</template>

<script>
import uniNavBar from '@/components/uni-ui/uni-nav-bar/uni-nav-bar.vue';
export default {
	props: {
		title: {
			type: String,
			default: ''
		}
	},
	components: {
		uniNavBar
	},
	methods: {
		showSideBar(){
			uni.showToast({
				title:'敬请期待'
			})
		}
	}
};
</script>

<style></style>
