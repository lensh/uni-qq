<template>
	<view>
		<nav-bar title="联系人"></nav-bar>
		<view class="p-1 bg-white"><uni-search-bar radius="15" @disableHandle="handleClick" :isDisabled="true" :placeholder="'搜索'"></uni-search-bar></view>
		<view class="bg-main pt-1">
			<view class="border-bottom"><uni-list-item title="新朋友"></uni-list-item></view>
			<scroll-view scroll-x :scroll-into-view="scrollInto" scroll-with-animation class="scroll-row border-bottom " style="height: 120rpx;">
				<view
					v-for="(item, index) in tabBars"
					:key="index"
					style="font-size: 30rpx;line-height: 40rpx;width: 80rpx;"
					class="scroll-row-item px-4 py-2 text-secondary mt-2 text-center"
					:id="'tab' + index"
					:class="tabIndex === index ? 'selected' : ''"
					@click="changeTab(index)"
				>
					{{ item.name }}
				</view>
			</scroll-view>
			<view class="bg-main" :style="'min-height:' + scrollH + 'px;'">
				<friend-list></friend-list>
			</view>
		</view>
	</view>
</template>

<script>
import uniSearchBar from '@/components/uni-ui/uni-search-bar/uni-search-bar.vue';
import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item.vue';
import friendList from '@/components/friend-list/friend-list.vue';
import navBar from '@/components/nav-bar/nav-bar.vue'
export default {
	components: { uniSearchBar, uniListItem, friendList,navBar },
	data() {
		return {
			// 顶部选项卡
			scrollInto: '',
			tabIndex: 0,
			scrollH: 0,
			tabBars: [
				{
					name: '好友'
				},
				{
					name: '分组'
				},
				{
					name: '群聊'
				},
				{
					name: '设备'
				},
				{
					name: '通讯录'
				},
				{
					name: '订阅号'
				}
			]
		};
	},
	onLoad() {
		uni.getSystemInfo({
			success: res => {
				this.scrollH = res.windowHeight - res.statusBarHeight - 140;
			}
		});
	},
	methods: {
		handleClick() {
			console.log('跳转');
		},
		// 切换选项
		changeTab(index) {
			if (this.tabIndex === index) {
				return;
			}
			this.tabIndex = index;
			// 滚动到指定元素
			this.scrollInto = 'tab' + index;
		}
	}
};
</script>
<style>
.selected {
	color: #000;
	border-radius: 30rpx;
	background-color: #dedfe4;
}
</style>
