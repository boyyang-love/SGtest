<template>
	<view class="container">
		<view class="recommend">
			<view>
				<text class="iconfont icon-remen2"></text>
				<text>热门推荐</text>
			</view>
			<view>
				<text class="iconfont">&#xe607;</text>
			</view>
		</view>
		<view class="hotel">
			<view class="hotel-recommed" v-for="(item, i) in hotelmes" :key='i'>
				<image :src="item.img" mode=""></image>
				<view class="hotel-mes">
					<text class="name">{{item.name}}</text>
					<text class="ranking">{{item.ranking}}</text>
					<view class="price">
						<text class="newPrice">{{item.newPrice}}</text>
						<text class="oldPrice">{{item.oldPrice}}</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				hotelmes: [{
						name: '【微逍遥.民宿酒店】',
						img: require("../../../static/imgs/hotel.png"),
						ranking: '巫山人气排名第一',
						newPrice: '￥199',
						oldPrice: '￥299'
					},
					{
						name: '【微逍遥.民宿酒店】',
						img: require("../../../static/imgs/hotel.png"),
						ranking: '巫山人气排名第一',
						newPrice: '￥299',
						oldPrice: '￥399'
					},
					{
						name: '【微逍遥.民宿酒店】',
						img: require("../../../static/imgs/hotel.png"),
						ranking: '巫山人气排名第一',
						newPrice: '￥399',
						oldPrice: '￥499'
					}, {
						name: '【微逍遥.民宿酒店】',
						img: require("../../../static/imgs/hotel.png"),
						ranking: '巫山人气排名第一',
						newPrice: '￥499',
						oldPrice: '￥599'
					},
				]
			};
		}
	}
</script>

<style lang="less">
	.container {
		min-height: 750rpx;
		background-color: #f6f6f6;
		margin-top: 24rpx;

		.hotel {
			display: flex;
			flex-wrap: wrap;
			width: 100%;
			justify-content: center;

			.hotel-recommed {
				margin: 15rpx 5rpx;
				width: 344rpx;
				height: 363rpx;
				background-color: white;
				box-sizing: border-box;
				border-radius: 35rpx;
				overflow: hidden;
				box-shadow: 0rpx 2rpx 3rpx 0rpx rgba(0, 0, 0, 0.5);

				image {
					width: 342rpx;
					height: 200rpx;
				}

				.hotel-mes {
					width: 100%;
					display: flex;
					justify-content: center;
					flex-direction: column;
					text-align: justify;

					.name {
						width: 100%;
						font-size: 30rpx;
					}

					.ranking {
						margin-left: 18rpx;
						width: 100%;
						font-size: 25rpx;
					}

					.price {
						margin-left: 18rpx;
						width: 100%;
						font-size: 30rpx;

						.newPrice {
							color: red;
						}

						.oldPrice {
							margin-left: 25rpx;
							color: gray;
							text-decoration: line-through;
						}
					}
				}
			}
		}

		.recommend {
			width: 100%;
			display: flex;
			justify-content: space-between;
			align-items: center;

			view {
				.icon-remen2 {
					color: red;
					font-size: 45rpx;
					margin-right: 10rpx;
				}

				margin: 30rpx;
			}
		}
	}

	@font-face {
		font-family: 'iconfont';
		/* project id 1769777 */
		src: url('//at.alicdn.com/t/font_1769777_mepc0feltdh.eot');
		src: url('//at.alicdn.com/t/font_1769777_mepc0feltdh.eot?#iefix') format('embedded-opentype'),
			url('//at.alicdn.com/t/font_1769777_mepc0feltdh.woff2') format('woff2'),
			url('//at.alicdn.com/t/font_1769777_mepc0feltdh.woff') format('woff'),
			url('//at.alicdn.com/t/font_1769777_mepc0feltdh.ttf') format('truetype'),
			url('//at.alicdn.com/t/font_1769777_mepc0feltdh.svg#iconfont') format('svg');
	}
</style>
