<template>
	<view class="content">
		<view class="pd_default bg-white">
			<view class=" bg-public weui-input text-minor">
				<text></text>
				<text>搜索商品</text>
			</view>
			<view class="banner">
				<Banner></Banner>
			</view>
			<!--分类-->
			<view class="">
				<view class="text-center padding-top-sm">
					<text class="tag-text text-bold"> SMART HOME</text>
				</view>
				<view class="cu-list grid" :class="['col-' + gridCol,gridBorder?'':'no-border']">
					<view class="cu-item text-center flex align-center" v-for="(item,index) in cuIconList" :key="index" v-if="index<gridCol*2">
						<view class="cu-list-item bg-public">
							<image class="cu-list-Image" :src="list[index]" mode=""></image>
						</view>

						<text class="cu-list-item-text text-default text-bold">{{item.name}}</text>
					</view>
				</view>
			</view>
		</view>

		<view class="pd_default bg-white margin-top-sm">
			<!--专享优惠劵-->
			<view class="tabb-content">
				<view class="tabbox flex justify-between align-center">
					<text class="tips text-default ft-xxl text-bold">专享优惠劵</text>
					<view class="text-gray ft-lg flex align-center">
						<text class="iconfont icon-right flex align-center justify-center"></text>
					</view>
				</view>
				<view>
					<scroll-view class="scroll-view_H" scroll-x="true" scroll-left="120">
						<block v-for="(item, index) in 5" :key="index">
							<view class="scroll-view-item_H uni-bg-red " :class="'bg-'+cuIconList[index].color">
								<view class="card-tips flex justify-around align-end padding-lr-sm">
									<view class="text-xxl text-price margin-right-sm">8</view>
									<view class="ft-sm">
										<view class="ft-lg">优惠劵</view>
										<view>满200元使用</view>
									</view>
								</view>


							</view>
						</block>
					</scroll-view>
				</view>
			</view>
			<!--限时秒杀-->
			<view class="tabb-content">
				<view class="tabbox flex justify-between align-center">
					<text class="tips text-default ft-xxl text-bold">限时秒杀</text>
					<view class="text-gray ft-lg flex align-center">
						<text class="iconfont icon-right flex align-center justify-center"></text>
					</view>
				</view>
			</view>
			<!--好物推荐-->
			<view class="tabb-content">
				<view class="tabbox flex justify-between align-center">
					<text class="tips text-default ft-xxl text-bold">好物推荐</text>
					<view class="text-gray ft-lg flex align-center">
						<text class="iconfont icon-right flex align-center justify-center"></text>
					</view>
				</view>
				<scroll-view class="recommend-item flex" scroll-x="true" scroll-left="120">
					<view style="display: inline-block; width: 33.33%;" v-for="item in 6" :key="item">
						<view class="recommend-box">
							<image class="recommend-box-img bg-public" src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/faa3e8d9298225c166c3ce926800d91c.png?thumb=1&w=200&h=200&f=webp&q=90"
							 mode=""></image>
							<view class="recommend-centen text-center">
								<view class="card-tag cu-tag light bg-tag-blue ft-xs">好物推荐</view>
								<view class="text-bold text-default ft-dl padding-tb-xs">短视的小贝吧</view>
								<view class="">
									<text class="text-price text-tag ft-xl margin-right-xs text-bold">360</text>
									<text class="text-price ft-dl text-minor text-decoration">490</text>
								</view>
							</view>
						</view>

					</view>
				</scroll-view>
			</view>
		</view>

		<view class="grid col-2 pd_default bg-white margin-tb-sm  order-box">
			<view class="order-item padding-right-sm margin-bottom-sm" v-for=" item in 6" :key="item">
					<image class=" radius bg-public" src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6cc07289d1a7d050d24e3fedf1f73086.png?thumb=1&w=200&h=200&f=webp&q=90"
			 mode="">
				</image>
				<view class="order-item-centet padding-tb-sm">
					<view class="text-default ft-xl text-bold">刷卡机肯德</view>
					<view class="text-minor ft-dl padding-tb-xs">这是什么疯了</view>
					<view class="card-tag cu-tag light bg-tag-red ft-xs">好物推荐</view>
				</view>
				<view class="">
					<text class="text-price text-tag ft-xxl margin-right-xs text-bold">360</text>
					<text class="text-price ft-dl text-minor text-decoration">490</text>
				</view>
			</view>
		</view>



	</view>

</template>

<script>
	import Banner from "./banner.vue"
	export default {
		components: {
			Banner,
		},
		data() {
			return {
				title: 'Hello',
				list: [
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6cc07289d1a7d050d24e3fedf1f73086.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/3b76c32a6b8beb73d00e22d7199bcba8.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/563ced6ca5112591d4c19f7133e8847b.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/4341891528452ee712596b4ed7347532.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/f3106695ccf44ebc7bf4683b0d925dfc.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj0.fds.api.mi-img.com/b2c-mimall-media/6f40f1fa8fc41913dcd40c5d7a4d2604.png?thumb=1&w=200&h=200',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/f607feb5f31aa04949d530799d010d99.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/e7d6458c24d0c24db9385ef7355dfd43.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/7dc06a754beb7fe2a2a8aeb93108e74f.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/faa3e8d9298225c166c3ce926800d91c.png?thumb=1&w=200&h=200&f=webp&q=90',
					'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6cc07289d1a7d050d24e3fedf1f73086.png?thumb=1&w=200&h=200&f=webp&q=90'
				],
				cuIconList: [{
						cuIcon: 'cardboardfill',
						color: 'red',
						badge: 120,
						name: 'VR'
					},
					{
						cuIcon: 'recordfill',
						color: 'orange',
						badge: 1,
						name: '录像'
					},
					{
						cuIcon: 'picfill',
						color: 'yellow',
						badge: 0,
						name: '图像'
					},
					{
						cuIcon: 'noticefill',
						color: 'olive',
						badge: 22,
						name: '通知'
					},
					{
						cuIcon: 'upstagefill',
						color: 'cyan',
						badge: 0,
						name: '排行榜'
					},
					{
						cuIcon: 'clothesfill',
						color: 'blue',
						badge: 0,
						name: '皮肤'
					},
					{
						cuIcon: 'discoverfill',
						color: 'purple',
						badge: 0,
						name: '发现'
					},
					{
						cuIcon: 'questionfill',
						color: 'mauve',
						badge: 0,
						name: '帮助'
					},
					{
						cuIcon: 'commandfill',
						color: 'purple',
						badge: 0,
						name: '问答'
					},
					{
						cuIcon: 'brandfill',
						color: 'mauve',
						badge: 0,
						name: '版权'
					}
				],
				gridCol: 5,
				gridBorder: false
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style scoped>
	.weui-input {
		height: 82rpx;
		width: 100%;
		text-align: center;
		line-height: 82rpx;
		letter-spacing: 4rpx;
		font-size: 28rpx;
		border-radius: 4rpx;
	}

	.banner {
		margin-top: 36rpx;
	}



	.tag-text {
		font-size: 22rpx;
		letter-spacing: 5rpx;
	}

	.tabb-content {
		padding-bottom: 20rpx;
	}

	.tabbox {
		padding: 20rpx 0;
	}

	.tips {
		position: relative;
		padding-left: 20rpx;
	}

	.tips::before {
		content: " ";
		position: absolute;
		top: 50%;
		margin-top: -16rpx;
		left: 0;
		background: #294D7C;
		width: 8rpx;
		height: 32rpx;
	}

	.scroll-view_H,
	.recommend-item {
		white-space: nowrap;
		width: 100%;
	}

	.scroll-view_H,
	.scroll-view-item_H {
		height: 136rpx;
	}

	.scroll-view-item_H {
		display: inline-block;
		width: 216rpx;
		margin-right: 20rpx;
	}

	.scroll-view-item_H:last-child {
		margin-right: 0;
	}

	.card-tips {
		height: 100%;
		padding: 32rpx 20rpx;
		vertical-align: baseline
	}

	.recommend-item,
	.recommend-box {
		height: 360rpx;
	}

	.recommend-box {
		/* width: 33.33%; */
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 28rpx 0;
		justify-content: space-between;

	}

	.recommend-box-img {
		display: block;
		width: 160rpx;
		height: 160rpx;
	}

	.order-item {
		width: 50%;
		height: 560rpx;
	}
	.order-item:nth-child(2n){
		padding-right:0;
	}

	.order-item image {
		display: block;
		width: 340rpx;
		height: 340rpx;
	}
</style>
