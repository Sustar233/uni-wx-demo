<template>
	<view @click="showM">
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
					duration: 1500,
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
			},
			showM() {
				uni.$showMsg()
				console.log('qwq')
			},
			async getNavList() {
				const {data: res} = await uni.$http.get('/api/public/v1/home/catitems')
				if (res.meta.status !== 200) return uni.$showMsg()
				this.navList = res.message
			},
		}
	}
</script>

<style lang="scss">

</style>
