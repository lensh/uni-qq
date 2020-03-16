<template>
	<uni-collapse>
		<uni-collapse-item title="特别关心" :open="false" :isIconLeft="true" :showAnimation="true">
			<view slot="right" class="text-secondary font-sm">1/1</view>
			<view class="flex align-center ml-5 pb-1">
				<image src="/static/default.jpg" class="rounded-circle face"></image>
				<view class="flex flex-column ml-1">
					<text class="nick">宇文玥</text>
					<text class="text-ellipsis text-secondary font-sm" style="max-width: 530rpx;">[手机在线]今天的日积月累,早晚会成为别人的今天的日积月累,早晚会成为别人的</text>
				</view>
			</view>
		</uni-collapse-item>
		<uni-collapse-item title="一笑倾城" :open="false" :isIconLeft="true" :showAnimation="true">
			<view slot="right" class="text-secondary font-sm">1/1</view>
			<view class="flex align-center ml-5 pb-1">
				<image src="/static/images/face.jpg" class="rounded-circle face"></image>
				<view class="flex flex-column ml-1">
					<text class="nick">楚乔</text>
					<text class="text-ellipsis text-secondary font-sm" style="max-width: 530rpx;">[手机在线]今天的日积月累,早晚会成为别人的今天的日积月累,早晚会成为别人的</text>
				</view>
			</view>
		</uni-collapse-item>
	</uni-collapse>
</template>

<script>
import uniCollapse from '@/components/uni-ui/uni-collapse/uni-collapse.vue';
import uniCollapseItem from '@/components/uni-ui/uni-collapse-item/uni-collapse-item.vue';
export default{
	components: { uniCollapse, uniCollapseItem },
}
</script>

<style scoped>
	.nick{
		font-size: 34rpx;color: red;line-height: 32rpx;
	}
	.face{
		width: 80rpx;height: 80rpx;
	}
</style>
