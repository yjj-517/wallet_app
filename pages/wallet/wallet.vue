<template>
	<view id="wallet">
		<!-- 钱包 -->
		<!-- 头部标签 -->
		<view class="head">
			<u-icon @click="showManage = true" name="list" size="52" :bold="true"></u-icon>
			<view class=""><text>钱包</text></view>
			<u-icon name="scan" size="52" :bold="true"></u-icon>
		</view>
		<!-- 头部左侧弹窗-账户管理 -->
		<u-overlay :show="showManage">
			<view class="account_manage_box">
				<view class="manage_box_head">
					<u-icon name="close" size="32" @click="showManage = false"></u-icon>
					<text>选择钱包</text>
					<text>管理</text>
				</view>
				<scroll-view :scroll-top="0" scroll-y="true" class="scroll-Y">
					<view class="account_box" @click="changeAccount">
						<view>ETH</view>
						<view>0xE9f6d5F43b6D61d6cC146aafCB3E5Af3C8f774E5</view>
					</view>
				</scroll-view>
			</view>
		</u-overlay>
		<!-- 下方展示栏-->
		<!-- 账户  -->
		<view class="account">
			<view class="account_box1">
				<text>ETH</text>
				<u-icon name="more-dot-fill" size="52" :bold="true" color="#fff"></u-icon>
			</view>
			<view class="account_box2" >
				<text>0xE9f6d5F43b6D61d6cC146aafCB3E5Af3C8f774E5</text>
				<u-icon name="more-dot-fill" size="48" :bold="true" color="#fff"></u-icon>
			</view>
			<view class="account_box3">
				<text>$</text>
				<text>7123456</text>
			</view>
		</view>
		<!-- 以太坊 -->
		<view class="eth_box">
			<u--image class="eth_imgs" src="../../static/logo.png" width="50" height="50" :lazy-load="true"></u--image>
			<text>以太坊2.0</text>
		</view>
		<!-- 代币选项卡-->
		<view class="token">
			<view class="token_tab">
				<u-tabs :list="tokenList" @click="changeTab" lineColor="#303133" :lineHeight="5" lineWidth="20px"></u-tabs>
				<u-icon name="plus-circle" size="48"></u-icon>
			</view>
			<!-- 选项卡内容 -->
			<view class="token_content">
				<!-- 第一个 -->
				<view class="token_box1">
					<view class="token_box1_content">
						<u--image class="token_imgs" shape="circle" src="../../static/logo.png" width="100" height="100"
							:lazy-load="true"></u--image>
						<view class="token_eth">
							<text>ETH</text>
							<view class="token_eth_money">
								<text>0.0236</text>
								<text>$ 73.11</text>
							</view>
						</view>
					</view>
				</view>
				<!-- 第二个 -->
				<view class="token_box2"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showManage: false,//账号弹框
				tokenList: [{
						name: '代币'
					},
					{
						name: 'DeFi'
					},
					{
						name: 'NFT'
					}
				]
			};
		},
		onLoad() {},
		methods: {
			// 切换账号
			changeAccount(){
				console.log("切换账号");
				this.showManage = false;
			},
			changeTab(item) {
				console.log('item', item);
			}
		}
	};
</script>

<style scoped lang="less">
	#wallet {

		// 头部
		.head {
			background-color: #fcfcfc;
			line-height: 100rpx;
			display: flex;
			justify-content: space-between;
			border-bottom: 2rpx solid #f3f3f3;
			padding: 0 4%;
		}

		// 头部左侧弹窗-账户管理
		.account_manage_box {
			position: relative;
			top: 10%;
			height: 90%;
			background-color: #fff;

			.manage_box_head {
				padding: 0 5%;
				width: 90%;
				display: flex;
				justify-content: space-between;
				height: 8%;
				border-bottom: 2rpx solid #f3f3f3;

				text {
					margin: auto 0;
				}

				text:nth-of-type(2) {
					color: #0790c4;
				}
			}

			scroll-view {
				height: 90%;
				margin: 2% 5%;
				width: 90%;

				.account_box {
					margin-bottom: 20rpx;
					padding: 20rpx 40rpx;
					background-color: #0790C4;
					border-radius: 20rpx;

					&:last-of-type {
						margin: 0;
					}

					view:nth-of-type(1) {
						font-weight: 500;
						color: #fff;
					}

					view:nth-of-type(2) {
						color: #52C1EC;
						font-size: 24rpx;
						overflow: hidden;
						text-overflow: ellipsis;
						white-space: nowrap;
					}
				}
			}
		}

		// 账户
		.account {
			margin: 2% 4%;
			background-color: #0790c4;
			border-radius: 20rpx;
			color: #fff;
			padding: 5%;

			.account_box1 {
				display: flex;
				justify-content: space-between;
				line-height: 48rpx;
			}

			.account_box2 {
				display: flex;
				line-height: 48rpx;
				color: #74cbef;

				text {
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
					width: 300rpx;
				}
			}

			.account_box3 {
				text-align: right;

				text:nth-of-type(1) {
					vertical-align: top;
					margin-right: 4rpx;
				}

				text:nth-of-type(2) {
					font-size: 48rpx;
				}
			}
		}

		// 以太坊
		.eth_box {
			display: flex;
			margin: 4%;
			border: 2rpx solid #f7f7f9;
			border-radius: 20rpx;
			color: #47484d;
			padding: 24rpx 0;

			.eth_imgs {
				margin: auto 50rpx;
			}
		}

		// 代币分段器
		.token {
			margin: 0 5%;

			.token_tab {
				display: flex;
				justify-content: space-between;
			}

			.token_content {
				.token_box1 {
					.token_box1_content {
						display: flex;
						line-height: 160rpx;

						.token_imgs {
							margin: auto 0;
						}

						.token_eth {
							width: 100%;
							display: flex;
							justify-content: space-between;
							border-bottom: 2rpx solid #f7f7f9;
							margin: 0 0 0 20rpx;

							.token_eth_money {
								display: flex;
								flex-direction: column;

								text {
									line-height: 48rpx;
									text-align: right;

									&:nth-of-type(1) {
										margin: 40rpx 0 0 0;
										font-size: 36rpx;
										font-weight: 500;
									}

									&:nth-of-type(2) {
										font-size: 24rpx;
										color: #aeb3b7;
									}
								}
							}
						}
					}
				}
			}
		}
	}
</style>
