<template>
	<view >
		<view class="cat-list-item padding-tb solid-bottom bg-white" v-for="item in 3" :key="item">
			<view class="cat-list-item-right flex padding-lr-sm align-center">
				<image src="../../../static/logo.png" mode=""></image>
				<view class="text-default text-dl margin-left-sm">
					<text class="text-dl text-bold">高清家用摄像头</text>
					<view class="text-sm text-minor margin-tb-xs">
						<text class="margin-right-sm">颜色:白色</text>
						<text class="margin-right-sm">规格:白色</text>
					</view>
					<view class="flex justify-between align-center">
						<text class="text-price text-tag ft-xl margin-right-xs">680</text>
						<text class="text-minor ft-sm">x1</text>
					</view>

				</view>
			</view>
		</view>

	</view>
</template>

<script>
</script>

<style>
	.cat-list-item {}

	.cat-list-item image {
		display: block;
		width: 114rpx;
		height: 114rpx;
	}

	.cat-list-item-right>view {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>
