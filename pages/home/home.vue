<template>
	<view>
		<view class="nav-list">
			<view class="nav-item" v-for="(item, i) in navList" :key="i" @click="navClickHandle(item)">
				{{item}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList: [
					'qwq',
					'qaq',
					'QWQ'
				]
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
			navClickHandle(item) {
				if (item === 'qwq') {
					uni.switchTab({
						url: '/pages/cate/cate'
					})
				}
			},
			// showM() {
			// 	uni.$showMsg()
			// 	console.log('qwq')
			// },
			async getNavList() {
				const {
					data: res
				} = await uni.$http.get('/api/public/v1/home/catitems')
				if (res.meta.status !== 200) return uni.$showMsg()
				this.navList = res.message
			},
		}
	}
</script>

<style lang="scss">
	.nav-list {
		display: flex;
		margin-top: 10rpx;
		justify-content: space-around;
	}

	.nav-item {
		padding: 10rpx;
		background-color: pink;
	}
</style>
