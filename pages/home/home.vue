<template>
	<view>
		home
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad() {
			this.init()
		},
		methods: {
			async init() {
				uni.showToast({
					title: '数据请求失败！',
					duration: 2500,
					icon: 'none'
				})
				const res = await uni.$http.get('/api/public/v1/home/swiperdata')
				console.log(res)
				// 请求成功
				if (res.meta.status !== 200) {
					return uni.showToast({
						title: '数据请求失败！',
						duration: 2500,
						icon: 'none'
					})
				}
			}
		}
	}
</script>

<style lang="scss">

</style>
