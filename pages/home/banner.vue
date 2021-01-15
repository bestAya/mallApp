<template>
	<view class="">
		<swiper class="square-dot" :indicator-dots="true" :circular="true" :autoplay="true" interval="5000" duration="500"
		 @change="cardSwiper" indicator-color="#ffffff" indicator-active-color="#ffffff">
			<swiper-item v-for="(item,index) in swiperList" :key="index" :class="cardCur==index?'cur':''">
				<view class="swiper-item">
					<image :src="item.url" mode="aspectFill" v-if="item.type=='image'"></image>
					<video :src="item.url" autoplay loop muted :show-play-btn="false" :controls="false" objectFit="cover" v-if="item.type=='video'"></video>
				</view>
			</swiper-item>
		</swiper>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				swiperList: [{
					id: 0,
					type: 'image',
					url: 'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/c57abbc9b9e06aa5ca23715b569d4c6c.jpg?w=2452&h=920'
				}, {
					id: 1,
					type: 'image',
					url: 'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/91e8be56a21db1b399fd25bfffe85bcc.jpeg?thumb=1&w=1226&h=460&f=webp&q=90',
				}, {
					id: 2,
					type: 'image',
					url: 'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/1acdc8c5e49afede6d6b75ed32568b22.jpg?thumb=1&w=1226&h=460&f=webp&q=90'
				}],
				cardCur: 0,
			}

		},
		methods: {
			cardSwiper(e) {
				this.cardCur = e.detail.current
			}
		},
	}
</script>

<style>
	.card-swiper {
		height: 304rpx;
	}

	.swiper-item {
		width: 100%;
		height: 304rpx;
		padding: 0;
	}
</style>
