<template>
	<view class="shoppingcar">
		<view class="goods" v-for="(item, i) in goods" :key="i" v-show="item.isDelete">
			<movable-area>
				<view class="del" @click="del(item)">
					<text>删除</text>
				</view>
				<view class="checked">
					<view class="box" @click="choose(item)">
						<text class="iconfont" v-show="item.checked">&#xe64c;</text>
					</view>
				</view>
				<movable-view x="103" class="max" direction="horizontal" out-of-bounds="true">
					<view class="goodsMes">
						<image src="../../static/imgs/2.jpg" mode=""></image>
						<view class="goodsAll">
							<view class="goodsDes">
								<text class="name">{{item.name}}</text>
								<text class="price">￥{{item.price | setPoint}} <text class="point">.{{item.price | point}}</text></text>
								<text class="size">{{item.size}}</text>
							</view>
							<view class="goodsNumber">
								<text class="number">x{{item.number}}</text>
							</view>
						</view>
					</view>
				</movable-view>
			</movable-area>
		</view>
		<view class="pay">
			<view class="allPrice">
				<view>
					<text class="rmb">￥</text>
					<text class="r-price">{{allPrice | setPoint}} <text class="point">. {{allPrice | point}}</text></text>
				</view>
				<view>
					<text class="e-price">|不含配送费</text>
				</view>
			</view>
			<view class="goPay">
				<navigator url="../payying/payying"><text>去支付</text></navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		components: {

		},
		data() {
			return {
				goods: [{
						checked: true,
						isDelete: true,
						name: "满天星鲜花束 1111束",
						price: 220.50,
						size: "规格：16枝 丨 颜色：红色",
						number: 1

					},
					{
						checked: false,
						isDelete: true,
						name: "满天星鲜花束 2222束",
						price: 110.50,
						size: "规格：16枝 丨 颜色：红色",
						number: 2

					},
					{
						checked: false,
						isDelete: true,
						name: "满天星鲜花束 3333束",
						price: 320.05,
						size: "规格：16枝 丨 颜色：红色",
						number: 3

					}
				]
			}
		},
		methods: {
			choose(item) {
				item.checked = !item.checked
			},
			del(item) {
				item.isDelete = false
				item.checked = false
			}

		},
		computed: {
			// 总价
			allPrice: {
				get() {
					let AllPRICE = 0
					for (let i = 0; i < this.goods.length; i++) {
						if (this.goods[i].checked == true) {
							AllPRICE += this.goods[i].price * this.goods[i].number
						}
					}
					return AllPRICE
				}
			}
		},
		filters: {
			// 整数部分
			setPoint(val) {
				return parseInt(val);
			},
			// 小数部分
			point(val) {
				let number = parseFloat(val).toFixed(2);
				let str = number.toString();
				str = str.split(".");
				return str[1];
			}
		}
	}
</script>

<style lang="less">
	.shoppingcar {
		width: 100%;
		min-height: 1000rpx;
		position: relative;
		// 支付
		.pay {
			width: 100%;
			height: 145rpx;
			background-color: red;
			position: fixed;
			bottom: 0;
			left: 0;
			display: flex;
			align-items: center;

			.allPrice {
				.rmb {
					font-size: 30rpx;
					color: white;
					margin: 10rpx;
				}

				.r-price {
					font-size: 40rpx;
					color: white;
					.point {
						font-size: 30rpx;
					}
				}

				.e-price {
					color: #888888;
				}

				height: 100%;
				flex: 3;
				display: flex;
				align-items: center;
				justify-content: space-around;
				background-color: #444444;
			}

			.goPay {
				flex: 2;
				height: 100%;
				background-color: #ef2b67;
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}

		// 商品信息
		.goods {
			movable-area {
				width: 750rpx;
				height: 200rpx;
				border-bottom: 1px solid black;
				position: relative;

				.checked {
					width: 103rpx;
					height: 200rpx;
					display: flex;
					justify-content: center;
					align-items: center;

					.box {
						width: 52rpx;
						height: 52rpx;
						border: 1px solid black;
						border-radius: 100%;
						display: flex;
						justify-content: center;
						align-items: center;

						text {
							font-size: 50rpx;
							color: yellow;
						}
					}

				}

				.del {
					display: flex;
					justify-content: center;
					align-items: center;
					width: 150rpx;
					height: 200rpx;
					background-color: red;
					position: absolute;
					top: 0;
					right: 0;
					z-index: 0;
				}

				movable-view {
					background-color: white;
					width: 600rpx;
					height: 200rpx;
					z-index: 4;

					.goodsMes {
						width: 100%;
						height: 200rpx;
						display: flex;
						align-items: center;

						image {
							width: 137rpx;
							height: 137rpx;
						}

						.goodsAll {
							width: 100%;
							display: flex;
							justify-content: space-between;
							align-items: center;

							.goodsDes {
								margin: 0rpx 25rpx;

								text {
									margin: 10rpx;
								}

								.name {
									font-size: 35rpx;
								}

								.price {
									color: red;
									font-size: 28rpx;
									.point {
										font-size: 20rpx;
									}
								}

								.size {
									color: #a7a7a7;
									font-size: 22rpx;
								}

								display: flex;
								flex-direction: column;
							}

							.goodsNumber {
								margin-right: 35rpx;
							}
						}
					}
				}
			}
		}
	}

	@font-face {
		font-family: 'iconfont';
		font-size: 24px;
		/* project id 1929037 */
		src: url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.eot');
		src: url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.eot?#iefix') format('embedded-opentype'),
			url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.woff2') format('woff2'),
			url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.woff') format('woff'),
			url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.ttf') format('truetype'),
			url('//at.alicdn.com/t/font_1929037_wcfdvp0pmx.svg#iconfont') format('svg');
	}
</style>
