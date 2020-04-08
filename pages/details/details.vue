<template>
	<view class="details">
		<image class="details_banner" src="/static/banner/banner_1.png"></image>
		<view class="details_content margin_bottom_10">
			<view class="title">【问道系列】健康长生</view>
			<view class="update">共10期 已更新到10期</view>
			<view class="free">免费</view>
			<view class="number update">14178人参与</view>
			<view class="gift">
				<image src="/static/gift.png"></image>
				<view class="update">赠好友</view>
			</view>
		</view>
		<view class="details_sticky margin_bottom_10">
			<scroll-view 
				scroll-x 
				class="tab_wrapper" 
				scroll-with-animation
				:scroll-left="100">
				<view class="tab_item">详情</view>
				<view class="tab_item">目录</view>
				<view class="tab_item">评价</view>
				<view class="tab_item">详情</view>
				<view class="tab_item">目录</view>
				<view class="tab_item">评价</view>
				<view class="tab_item">目录</view>
				<view class="tab_item">评价</view>
				<view class="tab_item">目录</view>
				<view class="tab_item">评价</view>
			</scroll-view>
		</view>
		<view class="details_wrapper">
			
		</view>
		<view class="details_footer">
			<view>免费</view>
			<view>立即参与</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		}
	}
</script>

<style lang="less" scoped>
	.details {
		
		.details_banner {
			height: 480rpx;
		}
		.details_content {
			background-color: #fff;
			padding: 20rpx;
			height: 220rpx;
			margin-top: -10rpx;
			position: relative;
			& > view {
				margin-top: 20rpx;
			}
			.title {
				font-weight: 600;
			}
			.update {
				color: #b0b0b0;
				font-size: 28rpx;
			}
			.free {
				color: #f33e54;
				font-size: 40rpx;
			}
			.gift {
				position: absolute;
				top: 30rpx;
				right: 30rpx;
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				image {
					width: 64rpx;
					height: 64rpx;
				}
			}
			.number {
				position: absolute;
				right: 30rpx;
				bottom: 30rpx;
			}
		}
		.details_sticky {
			height: 200rpx;
			background-color: #fff;
			position: sticky;
			.tab_wrapper {
				padding: 20rpx;
				width: 100%;
				height: 100rpx;
				overflow: hidden;
				white-space: nowrap;
				::-webkit-scrollbar {
					display: none;
				}
				.tab_item {
					height: 100%;
					min-width: 100rpx;
					text-align: center;
					display: inline-block;
				}
			} 
		}
		.details_wrapper {
			height: 2000rpx;
			background-color: #fff;
		}
		.details_footer {
			position: fixed;
			bottom: 0;
			width: 100%;
			display: flex;
			height: 100rpx;
			line-height: 100rpx;
			text-align: center;
			view {
				width: 50%;
				&:first-child {
					color: #f33e54;
					background-color: #ffe1d7;
				}
				&:last-child {
					color: #fff;
					background-color: #fda232;
				}
			}
		}
	}
</style>
