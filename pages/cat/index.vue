<template>
	<view class="content">
		<catcard></catcard>
	</view>
</template>

<script>
	import catcard from '../components/catcard/index.vue'
	export default {
		components: {
			catcard
		},
		data() {
			return {
				modalName: null,
				listTouchStart: 0,
				listTouchDirection: null,
			};
		},
		methods: {
			// ListTouch触摸开始，获取触摸点距盒子左侧的距离
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},
			// ListTouch计算方向，
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},
			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			}
		}
	}
</script>

<style>

</style>
