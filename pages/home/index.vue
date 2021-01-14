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
						<view class="cu-list-item bg-public"></view>

						<text class="cu-list-item-text text-default text-bold">{{item.name}}</text>
					</view>
				</view>
			</view>
		</view>

		<!---->
		<view class="pd_default bg-white margin-top-sm">
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
			<view class="tabb-content">
				<view class="tabbox flex justify-between align-center">
					<text class="tips text-default ft-xxl text-bold">限时秒杀</text>
					<view class="text-gray ft-lg flex align-center">
						<text class="iconfont icon-right flex align-center justify-center"></text>
					</view>
				</view>
			</view>
			<view class="tabb-content">
				<view class="tabbox flex justify-between align-center">
					<text class="tips text-default ft-xxl text-bold">好物推荐</text>
					<view class="text-gray ft-lg flex align-center">
						<text class="iconfont icon-right flex align-center justify-center"></text>
					</view>
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

	.cu-list-item {
		width: 104rpx;
		height: 104rpx;
		border-radius: 50%;
		margin-top: 30rpx;
	}

	.cu-list-item-text {
		font-size: 44rpx;
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

	.scroll-view_H {
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
</style>
