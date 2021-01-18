<template>
	<view class="content">
		<view class="cat-box">
			<view class="padding-lr-sm bg-white flex  align-center" v-for="item in 4" :key="item">
				<view class="padding-lr-sm">
					<checkbox class="checkbox round  bg-default" checked="true" />
				</view>
				<catcard class="catcard"></catcard>
			</view>
		</view>

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
				checked: 1,
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
	.catcard {
		flex: 1;
	}

	.cat-box .checkbox .wx-checkbox-input {
		margin: 0;
		width: 20px !important;
		height: 20px !important;
	}

	.cat-box checkbox::before {
		right: 3px;
	}
</style>
