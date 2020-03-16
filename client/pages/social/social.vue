<template>
	<view>
		<nav-bar title="动态"></nav-bar>
		<view class="p-1 bg-white"><uni-search-bar radius="15" @disableHandle="handleClick" :isDisabled="true" :placeholder="'搜索'"></uni-search-bar></view>
		<view class="bg-main" :style="'height:' + scrollH + 'px;'"><uni-list-item title="好友动态" thumb="/static/images/igs.png"></uni-list-item></view>
	</view>
</template>

<script>
import uniSearchBar from '@/components/uni-ui/uni-search-bar/uni-search-bar.vue';
import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item.vue';
import navBar from '@/components/nav-bar/nav-bar.vue';
export default {
	components: { uniSearchBar, uniListItem, navBar },
	data() {
		return {
			scrollH: 0
		};
	},
	methods: {
		handleClick() {
			console.log('跳转');
		}
	},
	onLoad() {
		uni.getSystemInfo({
			success: res => {
				this.scrollH = res.windowHeight - res.statusBarHeight - 40;
			}
		});
	}
};
</script>

<style></style>
