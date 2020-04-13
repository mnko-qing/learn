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
		<scroll-view
			scroll-x 
			enable-flex
			class="tab_wrapper" 
			:class="{'details_sticky': isFixed}"
			scroll-with-animation>
			<view 
				class="tab_item"
				:class="{'tab_item_active':currentTabIndex == index}"
				@tap="switchTab(index)"
				v-for="(item,index) in tabs"
				:key="item">
				{{item}}
			</view>
		</scroll-view>
		<swiper 
			class="tab_content"
			:style="{'height': swiperHeight + 'px'}"
			:duration="800"
			:current="currentTabIndex"
			@change="switchSwiper">
			<swiper-item>
				<view class="swiper_item" style="height: 1400rpx;">1</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper_item" style="height: 300rpx;">2</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper_item" style="height: 400rpx;">3</view>
			</swiper-item>
		</swiper>
		<view class="link_tabbar">
			<text>首页</text>|<text>发现</text>|<text>个人中心</text>
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
				tabs: ['详情', '目录', '评价'],
				currentTabIndex: 0,
				swiperHeight: 0,
				scrollTop: 0,
				top: 0,
				isFixed: false
			}
		},
		watch: {
			scrollTop(newval,oldval) {
				this.updateStickyState()
			}
		},
		onPageScroll({scrollTop}) {
			this.scrollTop = scrollTop
		},
		onReady() {
			this.getStickyTop()
		},
		mounted() {
			this.setSwiperHeight()
		},
		methods: {
			switchTab(index) {
				if(this.currentTabIndex !== index) {
					this.currentTabIndex = index
				}
			},
			switchSwiper(e) {
				this.currentTabIndex = e.detail.current
				this.setSwiperHeight()
			},
			setSwiperHeight() {
				let query = uni.createSelectorQuery().in(this)
				query.selectAll('.swiper_item').boundingClientRect( res => {
					this.swiperHeight = res[this.currentTabIndex].height
				}).exec()
			},
			updateStickyState() {
				this.isFixed = this.scrollTop >= this.top ? true : false
			},
			getStickyTop() {
				let query = uni.createSelectorQuery().in(this)
				query.select('.tab_wrapper').boundingClientRect( res => {
					this.top = res.top
				}).exec()
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
			position: fixed;
			top: 0;
			z-index: 999999;
		}
		.tab_wrapper {
			width: 100%;
			height: 80rpx;
			line-height: 80rpx;
			background-color: #fff;
			border-bottom: 1px solid #dfdee3;
			display: flex;
			overflow: hidden;
			white-space: nowrap;
			::-webkit-scrollbar {
				display: none;
			}
			.tab_item {
				flex: 1;
				min-width: 100rpx;
				padding: 0 20rpx;
				text-align: center;
				display: inline-block;
			}
		} 
		.tab_content {
			background-color: #fff;
		}
		.tab_item_active {
			color: #f33e54;
			position: relative;
			&::after {
				content: '';
				display: block;
				position: absolute;
				bottom: 1px;
				left: 20rpx;
				right: 20px;
				height: 1px;
				background-color: #f33e54;
			}
		}
		.link_tabbar {
			height: 100rpx;
			margin-bottom: 100rpx;
			display: flex;
			justify-content: center;
			align-items:center;
			text {
				padding: 0 10rpx;
			}
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
