<template>
	<view>
		<nav-bar title="消息"></nav-bar>
		<view class="p-1 bg-white"><uni-search-bar radius="15" @disableHandle="handleClick" :isDisabled="true" :placeholder="'搜索'"></uni-search-bar></view>
		<view class="flex align-center p-1 border-bottom bg-main">
			<image src="/static/default.jpg" class="rounded-circle ml-2" style="width: 100rpx;height: 100rpx;"></image>
			<view class="flex flex-1 flex-column pl-2">
				<text class="font-md" style="color: #0E1122;">宇文玥</text>
				<text class="font-sm text-secondary text-ellipsis" style="max-width: 490rpx;">没有</text>
			</view>
			<view class="flex align-center flex-column mr-2 font-sm">
				<text class="text-secondary">昨天</text>
				<view style="background-color: #F74C32; width: 40rpx;height: 40rpx;" class="rounded-circle text-white flex align-center justify-center"><text>1</text></view>
			</view>
		</view>
	</view>
</template>

<script>
import uniSearchBar from '@/components/uni-ui/uni-search-bar/uni-search-bar.vue';
import navBar from '@/components/nav-bar/nav-bar.vue'
export default {
	components: { uniSearchBar, navBar },
	methods: {
		handleClick() {
			console.log('跳转到搜索页');
		}
	}
};
</script>

<style></style>
