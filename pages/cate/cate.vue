<template>
	<view>
		<view :animation="animationData" @click="rotateAndScale" style="background:red;height:100rpx;width:100rpx"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				animationData: {}
			};
		},
		onShow: function() {
			var animation = uni.createAnimation({
				duration: 1000,
				timingFunction: 'ease',
			})
			this.animation = animation
			animation.scale(2, 2).rotate(45).step()
			this.animationData = animation.export()
			setTimeout(function() {
				animation.translate(30).step()
				this.animationData = animation.export()
			}.bind(this), 1000)
		},
		methods: {
			rotateAndScale: function() {
				var animation = uni.createAnimation({
					duration: 1000,
					timingFunction: 'ease',
				})
				this.animation = animation
				this.animation.rotate(45).scale(2, 2).step()
				this.animationData = this.animation.export()
				setTimeout(function() {
					animation.translate(30).step()
					this.animationData = animation.export()
				}.bind(this), 1000)
				
				// 旋转同时放大
			},
			// rotateThenScale: function() {
			// 	// 先旋转后放大
			// 	this.animation.rotate(45).step()
			// 	this.animation.scale(2, 2).step()
			// 	this.animationData = this.animation.export()
			// },
			// rotateAndScaleThenTranslate: function() {
			// 	// 先旋转同时放大，然后平移
			// 	this.animation.rotate(45).scale(2, 2).step()
			// 	this.animation.translate(100, 100).step({
			// 		duration: 1000
			// 	})
			// 	this.animationData = this.animation.export()
			// }
		}
	}
</script>

<style lang="scss">

</style>
