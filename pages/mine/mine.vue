<template>
	<view class="mine">
		<view class="user">
			<image src="../../static/imgs/5.png" mode=""></image>
			<view class="head">
				<view class="headImg">
					<image src="../../static/imgs/1.jpg" mode=""></image>
				</view>
				<view class="nickname">
					<text>爱旅游的草</text>
				</view>
			</view>
		</view>
		<view class="order">
			<view class="myOrder">
				<text class="iconfont ord">&#xe64b; <text class="my"> 我的订单</text></text>
			<!-- 	<text class="iconfont" @click="goToOrder">&#xe635;</text> -->
				<navigator url="../shoppingCar/shoppingCar"><text class="iconfont">&#xe635;</text></navigator>
			</view>
			<view class="orderDetail">
				<view class="waitingSolve">
					<view class="waiting" v-for="(item, i) in waitingOrder" :key='i'>
						<text>{{item.number}}</text>
						<text>{{item.name}}</text>
					</view>
				</view>
			</view>
		</view>
		<view class="card">
			<view class="carBox" v-for="(item, i) in card" :key='i'>
				<view class="box">
					<view class="left">
						<text :class="item.icon1"></text>
					</view>
					<view class="right">
						<text>{{item.name1}}</text>
						<text class="iconfont">&#xe635;</text>
					</view>
				</view>
				<view class="box">
					<view class="left">
						<text :class="item.icon2"></text>
					</view>
					<view class="right">
						<text>{{item.name2}}</text>
						<text class="iconfont">&#xe635;</text>
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
				waitingOrder: [{
						name: "待付款",
						number: 10
					},
					{
						name: "待出发",
						number: 55
					},
					{
						name: "已完成",
						number: 30
					},
					{
						name: "已取消",
						number: 22
					}
				],
				card: [{
						name1: '我的收藏',
						name2: '推广中心',
						icon1: 'iconfont icon-shoucang',
						icon2: 'iconfont icon-laba_bg;'
					},
					{
						name1: '城市合伙人',
						name2: '商家入驻',
						icon1: 'iconfont icon-hehuoren;',
						icon2: 'iconfont icon-qunfengshangjia'
					},
					{
						name1: '设置',
						name2: '关于我们',
						icon1: 'iconfont icon-shezhi',
						icon2: 'iconfont icon-guanyuwomen1'
					}
				]
			};
		},
		methods: {
		
		},

	}
</script>

<style lang="less">
	page {
		background-color: #f6f6f6;
	}

	.mine {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		position: relative;

		.user {
			width: 100%;
			height: 382rpx;
			position: relative;

			image {
				width: 100%;
				height: 382rpx;
			}

			.head {
				width: 100%;
				height: 382rpx;
				position: absolute;
				top: 0;
				left: 0;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;

				.headImg {
					width: 122rpx;
					height: 122rpx;
					border: 2px solid white;
					border-radius: 100%;
					overflow: hidden;

					image {
						width: 122rpx;
						height: 122rpx;
					}
				}

				.nickname {
					font-size: 30rpx;
					color: white;
					margin: 15rpx;
				}
			}


		}

		.order {
			width: 691rpx;
			height: 197rpx;
			background-color: white;
			position: absolute;
			bottom: -130rpx;
			border-radius: 8rpx;
			box-shadow: 0rpx 1rpx 2rpx 0rpx rgba(0, 0, 0, 0.4);

			.myOrder {
				width: 100%;
				height: 40%;
				display: flex;
				justify-content: space-between;
				align-items: center;

				.ord {
					color: green;

					.my {
						color: black;
					}
				}

				text {
					font-size: 35rpx;
					margin: 0rpx 15rpx;
				}
			}

			.orderDetail {
				width: 100%;
				height: 50%;

				.waitingSolve {
					width: 100%;
					display: flex;
					justify-content: space-around;
					align-items: center;

					.waiting {
						padding: 2rpx;
						display: flex;
						flex-direction: column;
						text-align: center;
					}
				}
			}
		}

		.card {
			width: 100%;
			// height: 550rpx;
			position: absolute;
			top: 550rpx;
			left: 0;

			.carBox {
				width: 100%;
				border-bottom: 1px solid white;
				box-sizing: border-box;
				margin: 25rpx 0rpx;

				.box {
					background-color: white;
					width: 100%;
					height: 100rpx;
					display: flex;
					justify-content: space-between;
					align-items: center;

					view {
						// font-size: 24rpx;
						margin: 10rpx;
					}

					.left {
						flex: 2;
						height: 100%;
						display: flex;
						justify-content: center;
						align-items: center;

						text {
							font-size: 65rpx;
							color: #fff143;
						}
					}

					.right {
						width: 100%;
						height: 100%;
						flex: 10;
						display: flex;
						justify-content: space-between;
						align-items: center;
						box-sizing: border-box;
						border-bottom: 1px solid #eeeeee;
					}
				}
			}
		}

	}
</style>
