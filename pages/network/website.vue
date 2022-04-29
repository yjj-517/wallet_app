<template>
	<view id="website">
		<!-- 网站搜索 -->
		<!-- 头部搜索 -->
		<view class="search">
			<u--input placeholder="搜索或者输入网址" prefixIcon="search" prefixIconStyle="font-size: 22px;color: #909399"
				shape="circle" clearable></u--input>
			<text @click="goNetwork">取消</text>
		</view>
		<view class="search_history">
			<view class="search_box">
				<text>浏览历史</text>
				<view class="search_box_delete" v-if="deleteBut" @click="deleteBut = false">
					<u-icon name="trash" size="38" color="#909399"></u-icon>
				</view>
				<view class="search_box_delete delete_box" v-if="!deleteBut" @click="onDelste">
					<u-icon name="trash" size="36" color="#909399"></u-icon>
					<text>全部删除</text>
				</view>
			</view>
			<view class="search_box history_box" v-for="(item, index) in urls" :key="index">
				<text @click="goWeb(item)">{{ item }}</text>
				<u-icon @click="delsteWeb(index)" name="close" size="28" color="#909399"></u-icon>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				deleteBut: true,
				urls: ['https://www.baidu.com/', 'https://uviewui.com/', 'https://www.metatoys.game/#/home/index']
			};
		},
		methods: {
			// 取消-返回上一级
			goNetwork() {
				uni.switchTab({
					url: '/pages/network/network'
				});
			},
			// 删除所有网址记录
			onDelste() {
				this.urls = [];
				console.log("删除");
			},
			// 删除单条网址记录
			delsteWeb(i) {
				console.log(i);
				this.urls.splice(i, 1);
			},
			// 跳转网站
			goWeb(res) {
				// console.log(res);
				uni.navigateTo({
					url: '/pages/network/newWeb?res=' + res
				});
			},

		}
	};
</script>

<style scoped lang="less">
	#website {
		.search {
			position: fixed;
			top: 0;
			left: 0;
			display: flex;
			border-bottom: 2rpx solid #f3f3f3;
			line-height: 76rpx;
			padding: 20rpx 5%;
			width: 90%;
			background-color: #fff;
			z-index: 99;

			text {
				color: #2979ff;
				margin-left: 20rpx;
			}
		}

		.search_history {
			padding: 18% 5% 0;

			.search_box {
				display: flex;
				justify-content: space-between;
				line-height: 76rpx;
				color: #909399;

				.search_box_delete {
					margin: auto 0;
				}

				.delete_box {
					line-height: 48rpx;
					display: flex;
					font-size: 24rpx;
					background-color: #f3f4f5;
					border-radius: 20%;
				}
			}

			.history_box {
				border-bottom: 2rpx solid #f3f3f3;

				text {
					color: #000;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
					width: 80%;
				}
			}
		}
	}
</style>
