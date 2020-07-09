<template>
	<view class="allpost">
		<!-- 评论回复 -->
		<view class="post" v-for="(item, i) in post" :key='i'>
			<view class="headImg">
				<image src="../../../static/imgs/1.jpg" mode=""></image>
			</view>
			<view class="postMes">
				<view class="nickname">
					<text>{{item.nickname}}</text>
				</view>
				<view class="content">
					<text>{{item.content}}</text>
				</view>
				<view class="time">
					<text class="postTime">{{item.postTime}}</text>
					<text :class="{active: item.isLink}" @click="addActive(item)" class="iconfont">&#xe618;</text>
				</view>
				<view class="replyContent" v-show="item.replyContent !='' " v-for="(items, j) in item.replyContent" :key="j">
					<text>{{items}}</text>
					<text class="replyTime">{{item.replyTime}}</text>
				</view>
				<view class="reply">
					<text @click="reply(item)">回复</text>
				</view>
			</view>
		</view>
		<!-- 回复框 -->
		<view class="replyBox" v-show="isShow">
			<textarea v-model="replays" />
			<view class="send">
				<text @click="send" class="iconfont">&#xe61c;</text>
				<text @click="cancle" class="iconfont">&#xe635;</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isShow: false,
				replays: '',
				post: [{
						nickname: '笑起来很好看',
						content: '人生就是一场充满未知的旅行,在乎的是沿途的风景，在乎的是看风景的心情，旅行不会因为美丽的风景而终止',
						postTime: '2019-10-25  15:36:59',
						replyContent: ['人生就是一场充满未知的旅行,在乎的是沿途的风景','人生就是一场充满未知的旅行,在乎的是沿途的风景'],
						replyTime: '2019-10-25  15:36:59',
						icon: 'iconfont icon-dianzan1',
						isLink: true
					},
					{
						nickname: '笑起来很好看',
						content: '人生就是一场充满未知的旅行,在乎的是沿途的风景，在乎的是看风景的心情，旅行不会因为美丽的风景而终止',
						postTime: '2019-10-25  15:36:59',
						replyContent: [],
						replyTime: '',
						icon: 'iconfont icon-dianzan1',
						isLink: false
					},
					{
						nickname: '笑起来很好看',
						content: '人生就是一场充满未知的旅行,在乎的是沿途的风景，在乎的是看风景的心情，旅行不会因为美丽的风景而终止',
						postTime: '2019-10-25  15:36:59',
						replyContent: ['人生就是一场充满未知的旅行,在乎的是沿途的风景','人生就是一场充满未知的旅行,在乎的是沿途的风景'],
						replyTime: '2019-10-25  15:36:59',
						icon: 'iconfont icon-dianzan1',
						isLink: true
					}
				]
			};
		},
		methods: {
			addActive(item) {
				item.isLink = !item.isLink
			},
			reply(item) {
				this.isShow = true
			},
			send() {
				// this.isShow = false
				if(this.replays == ''){
					uni.showToast({
						title: '回复不能为空',
						icon: 'none'
					})
				}else {
					uni.showToast({
					title: '回复成功',
					success: ()=>{
						this.isShow = false
					}
				    })
				}
				
				
			},
			cancle() {
				// this.isShow = false
				uni.showModal({
					title: '提示',
					content: '退出回复面板',
					success:(res)=>{
						if(res.confirm){
							this.isShow = false
						}else {
							this.isShow = true
						}
					}
				})
			}
		},

	}
</script>

<style lang="less" scoped>
	.active {
		color: red;
	}

	.allpost {
		width: 100%;
		position: relative;
		// 帖子
		.post {
			width: 100%;
			display: flex;

			.headImg {
				flex: 1;
				margin: 20rpx;

				image {
					width: 105rpx;
					height: 105rpx;
					border: 2rpx solid white;
					border-radius: 100%;
				}
			}

			.postMes {
				flex: 9;

				view {
					margin: 20rpx;
				}

				.nickname {
					font-size: 35rpx;
					font-weight: bold;
				}

				.content {
					font-size: 35rpx;
				}

				.time {
					display: flex;
					justify-content: space-between;
					font-size: 35rpx;
					color: #999999;
					border-bottom: 1rpx dashed #999999;
					padding-bottom: 15rpx;
				}

				.replyContent {
					font-size: 35rpx;
					background-color: #f2f2f2;
					padding: 15rpx;
					display: flex;
					flex-direction: column;
					justify-content: flex-start;

					.replyTime {
						color: #999999;
						padding-top: 10rpx;
					}
				}

				.reply {
					font-size: 35rpx;
				}
			}
		}
		// 回复
		.replyBox {
			width: 75%;
			height: 300rpx;
			background-color: white;
			border: 1px solid #f2f2f2;
			box-shadow: 0rpx 2rpx 3rpx 0rpx rgba(0, 0, 0, 0.5);
			position: fixed;
			top: 0;
			left: 0;
			bottom: 0;
			right: 0;
			margin: auto;
			top: 400rpx;
			textarea {
				width: 80%;
				height: 210rpx;
			}
			.send {
				width: 100%;
				display: flex;
				justify-content: space-between;
				text {
					font-size: 45rpx;
					margin: 25rpx;
					color: red;
				}
			}
		}
		
	}
</style>
