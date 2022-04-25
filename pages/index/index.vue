<template>
	<view id="wallet">
		wallet
		<!-- 头部 -->
		<view class="head">
			<view class="">选择</view>
			<view class="">钱包</view>
			<view class="">扫码</view>
		</view>
		<!-- 中间 -->
		<view class="centre">
			<!-- 账户 -->
			<view class="account">
				<view class="account_network">
					<view class="">ETH</view>
					<u-icon name="more-dot-fill" color="#ffffff" size="18"></u-icon>
				</view>
				<view class="account_box"><text>0xE9f6d5F43b6D61d6cC146aafCB3E5Af3C8f774E5</text></view>
				<view class="account_money">
					<text>$</text>
					<text>89</text>
				</view>
			</view>
			<!-- 以太坊生态 -->
			<view class="ecology">
				<image src="../../static/logo.png" mode=""></image>
				<text>以太坊2.0</text>
			</view>
			<!-- tab -->
			<view class="tab">
				<view class="tab_box">
					<u-tabs :list="tabList" @click="onClickItem"></u-tabs>
					<u-icon name="plus-circle" v-if="current == 0"></u-icon>
				</view>
				<!-- 代币 -->
				<view class="tab_content_box" v-if="current == 0">
					<view class="cont_box">
						<u-image class="cont_imgs" src="../../static/logo.png" width="25" height="25" :lazy-load="true" shape="circle"></u-image>
						<view class="cont_money">
							<view class="">ETH</view>
							<view class="">
								<text>0.2333366</text>
								<text>$ 73.22</text>
							</view>
						</view>
					</view>
				</view>
				<!-- DeFi -->
				<view class="tab_content_box" v-if="current == 1">
					<view class="cont_box">
						<u-image class="cont_imgs" src="../../static/logo.png" width="25" height="25" :lazy-load="true" shape="circle"></u-image>
						<view class="cont_money">
							<view class="">DeFi</view>
							<view class="">
								<text>0.2333366</text>
								<text>$ 73.22</text>
							</view>
						</view>
					</view>
				</view>
				<!-- NFT -->
				<view class="tab_content_box" v-if="current == 2">
					<view class="cont_box">
						<u-image class="cont_imgs" src="../../static/logo.png" width="25" height="25" :lazy-load="true" shape="circle"></u-image>
						<view class="cont_money">
							<view class="">NFT</view>
							<view class="">
								<text>0.2333366</text>
								<text>$ 73.22</text>
							</view>
						</view>
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
			title: 'wallet',
			tabList: [{ name: '代币' }, { name: 'DeFi' }, { name: 'NFT' }],
			current: 0
		};
	},
	onLoad() {},
	methods: {
		// tab切换
		onClickItem(res) {
			this.current = res.index;
		}
	}
};
</script>

<style lang="less">
#wallet {
	.head {
		padding: 0 5%;
		line-height: 100rpx;
		background-color: #dddddd;
		border-bottom: 2rpx solid #444444;
		display: flex;
		justify-content: space-between;
	}
	.centre {
		margin: 0 5%;
		// 账户
		.account {
			margin: 28rpx 0;
			background-color: #0790c4;
			border-radius: 10rpx;
			color: #fff;
			padding: 0 2%;
			.account_network {
				display: flex;
				justify-content: space-between;
				padding: 40rpx 0 0 0;
				line-height: 60rpx;
			}
			.account_box {
				display: flex;
				text {
					font-size: 24rpx;
					width: 300rpx;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
				}
			}
			.account_money {
				text-align: right;
				padding-bottom: 24rpx;
				text:nth-of-type(1) {
					vertical-align: 12rpx;
					margin-right: 6rpx;
				}
				text:nth-of-type(2) {
					font-size: 48rpx;
				}
			}
		}
		// 以太坊
		.ecology {
			border: 2rpx solid #c0c0c0;
			border-radius: 10rpx;
			line-height: 100rpx;
			image {
				vertical-align: middle;
				margin-left: 50rpx;
				width: 50rpx;
				height: 50rpx;
			}
			text {
				margin-left: 50rpx;
				color: #4c4d52;
			}
		}
		//tab
		.tab {
			.tab_box {
				display: flex;
				justify-content: space-between;
			}
			.tab_content_box {
				.cont_box {
					display: flex;
					// line-height: 98rpx;
					// justify-content:space-between;
					.cont_imgs {
						margin: auto 0;
						border-radius: 50%;
					}
					.cont_money {
						margin-left: 20rpx;
						width: 100%;
						border-bottom: 2rpx solid #f4f4f5;
						display: flex;
						justify-content: space-between;
						view:nth-of-type(1) {
							margin: auto 0;
						}
						view:nth-of-type(2) {
							display: flex;
							flex-direction: column;
							text-align: right;
							line-height: 49rpx;
							text:nth-of-type(2) {
								font-size: 24rpx;
								color: #a1a7aa;
							}
						}
					}
				}
			}
		}
	}
}
</style>
