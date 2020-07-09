<template>
	<view class="circle">
		<view class="head">
			<image src="../../static/imgs/4.jpg" mode=""></image>
			<view class="user">
				<image src="../../static/imgs/1.jpg" mode=""></image>
			</view>
			<view class="nickname">爱旅游的草</view>
		</view>
		<view class="tab">
			<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="text" active-color="#ffc144"></uni-segmented-control>
			<view class="content">
				<view v-if="current === 0">
					<all-post></all-post>
				</view>
				<view v-if="current === 1">
					我的发布
				</view>
				<view v-if="current === 2">
					我的评论
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniSegmentedControl from "@/components/uni-segmented-control/uni-segmented-control.vue"
	import allPost from "@/pages/component/allPost/allPost"
	export default {
		components: {
			uniSegmentedControl,
			allPost
		},
		data() {
			return {
				items: ['全部帖子', '我的发布', '我的评论'],
				current: 0
			};
		},
		methods: {
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
			}
		},
	}
</script>

<style lang="less" scoped>
	.active {
		border-bottom: 2px solif yellow;
	}

	.circle {
		width: 100%;

		.head {
			width: 100%;
			height: 327rpx;
			position: relative;
			display: flex;
			justify-content: center;
			align-items: center;

			image {
				width: 100%;
				height: 100%;
			}

			.user {
				width: 124rpx;
				height: 124rpx;
				border: 2px solid white;
				border-radius: 100%;
				overflow: hidden;
				position: absolute;
			}

			.nickname {
				position: absolute;
				bottom: 30rpx;
				margin: 10rpx;
				font-size: 28rpx;
				font-weight: bold;
			}
		}

		.tab {
			width: 100%;
			height: 83rpx;
			view {
				margin: 10rpx 20rpx;
			}
		}
	}
</style>
