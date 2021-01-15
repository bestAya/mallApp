<template>
	<view>
		<view class="VerticalBox">
			<scroll-view class="VerticalNav nav" scroll-y scroll-with-animation :scroll-top="verticalNavTop" style="height:calc(100vh)">
				<view class="cu-item" :class="index==tabCur?'text-mode cur':''" v-for="(item,index) in list" :key="index" @tap="TabSelect"
				 :data-id="index">
					家电{{item.name}}
				</view>
			</scroll-view>
			<view class="">
				<scroll-view class="VerticalMain" scroll-y scroll-with-animation style="height:calc(100vh)" :scroll-into-view="'main-'+mainCur"
				 @scroll="VerticalMain">
				 <view class="bg-white">
				 	<image class="VerticalBanner " src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/c57abbc9b9e06aa5ca23715b569d4c6c.jpg?w=2452&h=920"
				 	 mode=""></image>
				 </view>
					
					<view class=" bg-white" v-for="(item,index) in list" :key="index" :id="'main-'+index">
						<!-- <view class="cu-bar solid-bottom bg-white">
							<view class="action">
								<text class="cuIcon-title text-green"></text> Tab-{{item.name}}</view>
						</view> -->
						<view class="padding-top text-center"><text :class="index==tabCur?'text-mode cur':''" class="text-bold"> - Tab-{{item.name}} - </text></view>
						<view class="cu-list grid" :class="['col-' + gridCol,gridBorder?'':'no-border']">
							<view class="cu-item text-center flex align-center" v-for="(item,index) in cuIconList" :key="index" v-if="index<gridCol*2">
								<view class="cu-list-item">
									<image class="cu-list-Image" src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/4341891528452ee712596b4ed7347532.png?thumb=1&w=200&h=200&f=webp&q=90"
									 mode=""></image>
								</view>
								<text class="cu-list-item-text text-default text-bold">{{item.name}}</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [],
				tabCur: 0,
				mainCur: 0,
				verticalNavTop: 0,
				load: true,
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
				gridCol: 3,
				gridBorder: false
			};
		},
		onLoad() {
			uni.showLoading({
				title: '加载中...',
				mask: true
			});
			let list = [{}];
			for (let i = 0; i < 26; i++) {
				list[i] = {};
				list[i].name = String.fromCharCode(65 + i);
				list[i].id = i;
			}
			this.list = list;
			this.listCur = list[0];
		},
		onReady() {
			uni.hideLoading()
		},
		methods: {
			TabSelect(e) {
				this.tabCur = e.currentTarget.dataset.id;
				this.mainCur = e.currentTarget.dataset.id;
				this.verticalNavTop = (e.currentTarget.dataset.id - 1) * 50
			},
			//希望有大佬给我讲解一下这个双向联动函数
			VerticalMain(e) {
				// #ifdef MP-ALIPAY
				return false //支付宝小程序暂时不支持双向联动 
				// #endif
				let that = this;
				let tabHeight = 0;
				if (this.load) {
					for (let i = 0; i < this.list.length; i++) {
						let view = uni.createSelectorQuery().select("#main-" + this.list[i].id);
						view.fields({
							size: true
						}, data => {
							this.list[i].top = tabHeight;
							tabHeight = tabHeight + data.height;
							this.list[i].bottom = tabHeight;
						}).exec();
					}
					this.load = false
				}
				let scrollTop = e.detail.scrollTop + 10;
				for (let i = 0; i < this.list.length; i++) {
					if (scrollTop > this.list[i].top && scrollTop < this.list[i].bottom) {
						this.verticalNavTop = (this.list[i].id - 1) * 50
						this.tabCur = this.list[i].id
						console.log(scrollTop)
						return false
					}
				}
			}
		},
	}
</script>

<style>
	.fixed {
		position: fixed;
		z-index: 99;
	}

	.VerticalNav.nav {
		width: 200upx;
		white-space: initial;
	}

	.VerticalNav.nav .cu-item {
		width: 100%;
		text-align: center;
		background-color: #fff;
		margin: 0;
		border: none;
		height: 50px;
		position: relative;
	}

	.VerticalNav.nav .cu-item.cur {
		background-color: #f1f1f1;
	}

	.VerticalNav.nav .cu-item.cur::after {
		content: "";
		width: 8upx;
		height: 30upx;
		border-radius: 10upx 0 0 10upx;
		position: absolute;
		background-color: currentColor;
		top: 0;
		right: 0upx;
		bottom: 0;
		margin: auto;
	}

	.VerticalBox {
		display: flex;
	}

	.VerticalMain {
		background-color: #f1f1f1;
		flex: 1;
	}

	.VerticalBanner {
		height: 196rpx;
		width: 100%;
		padding: 0 30rpx;
	}
</style>
