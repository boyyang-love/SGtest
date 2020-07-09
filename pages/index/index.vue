<template>
	<view class="container">
		<view class="banner">
			<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
				<swiper-item v-for="(item, i) in bannerImage" :key="i">
					<view class="swiper-item">
						<image :src="item" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
			<view class="search">
				<input type="text" placeholder="热门搜索" />
				<text class="iconfont icon-sousuo2"></text>
			</view>
		</view>
		<view class="nav-tabs">
			<view class="tab-change" v-for="(item, i) in tab" :key='i' @click="tabholder">
				<text :class="item.icon"></text>
				<text>{{item.name}}</text>
			</view>
		</view>
		<recommend></recommend>
	</view>
</template>

<script>
	import recommend from '@/pages/component/recommend/recommend'
	export default {
		components: {
			recommend
		},
		data() {
			return {
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				bannerImage: [
					require("static/imgs/1.jpg"),
					require("static/imgs/2.jpg"),
					require("static/imgs/3.jpg"),
					require("static/imgs/4.jpg")
				],
				tab: [{
					name: '山庄',
					icon: 'iconfont icon-fangwuguanli',
					checked: true
				}, {
					name: '周边',
					icon: 'iconfont icon-xingquzhoubian',
					checked: false
				}, {
					name: '伴游',
					icon: 'iconfont icon-wode',
					checked: false
				}, {
					name: '定制',
					icon: 'iconfont icon-fenzu',
					checked: false
				}]

			}
		},
		methods: {
			tabholder(){
				console.log('ok')
			}
		}
	}
</script>

<style lang='less'>
	.active {
		color: red;
	}

	.container {
		.nav-tabs {
			width: 100%;
			margin-top: 30rpx;
			display: flex;
			justify-content: space-around;

			.tab-change {
				display: flex;
				flex-direction: column;

				text {
					font-size: 30rpx;
					color: #333333;
				}

				.iconfont {
					color: #ffc144;
					font-size: 65rpx;
				}
			}
		}

		.banner {
			height: 420rpx;
			position: relative;

			.search {
				position: absolute;
				left: 0;
				top: 15rpx;
				width: 100%;
				height: 68rpx;
				display: flex;
				justify-content: center;

				input {
					width: 691rpx;
					height: 100%;
					background-color: #fff1f4;
					box-sizing: border-box;
					border-radius: 40rpx;
					background: rgba(255, 241, 244, 0.6);
					padding-left: 45rpx;
				}

				.icon-sousuo2 {
					position: absolute;
					right: 50rpx;
					top: 18rpx;
				}
			}

			.swiper {
				height: 420rpx;

				.swiper-item {
					width: 100%;
					height: 420rpx;

					image {
						width: 100%;
						height: 420rpx;
					}
				}
			}
		}
	}
</style>
