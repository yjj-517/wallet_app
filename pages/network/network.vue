<template>
	<view id="network">
		<!-- 浏览 -->
		<!-- 轮播图 -->
		<view class="network_banner">
			<u-swiper :list="list5" height="400"></u-swiper>
			<view class="search" @click="goWebsite">
				<u-icon name="question-circle" color="#A8A9AD" size="50"></u-icon>
				<text>搜索或者输入网址</text>
				<view class="search_icon" @click.stop="b"><u-icon name="scan" size="56" color="#000"></u-icon></view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			current: 0,
			list5: ['https://cdn.uviewui.com/uview/swiper/swiper3.png', 'https://cdn.uviewui.com/uview/swiper/swiper2.png', 'https://cdn.uviewui.com/uview/swiper/swiper1.png']
		};
	},
	methods: {
		goWebsite() {
			// console.log(123);
			uni.navigateTo({
				url: '/pages/network/website'
			});
		},
		b() {
			console.log(3);
		}
	}
};
</script>

<style scoped lang="less">
#network {
	// 轮播图
	.network_banner {
		position: relative;
		// 搜索框
		.search {
			width: 80%;
			display: flex;
			justify-content: space-between;
			border: 2rpx solid #f3f3f3;
			border-radius: 50rpx;
			color: #a8a9ad;
			background-color: #fff;
			padding: 0 5%;
			position: absolute;
			line-height: 100rpx;
			left: 5%;
			bottom: -50rpx;
			.search_icon {
				margin: auto 0;
			}
		}
	}
}
</style>
