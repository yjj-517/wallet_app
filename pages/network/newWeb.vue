<template>
	<view id="newWeb">
		<web-view :src="httpUrl" v-if="httpUrl"></web-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				httpUrl:"",
			}
		},
		methods: {

		},
		onLoad(option) { //option为object类型，会序列化上个页面传递的参数
			console.log(option); //打印出上个页面传递的参数。
			this.httpUrl = option.res
		}
	}
</script>

<style>

</style>
