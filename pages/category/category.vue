<template>
	<view class="category">
		<uni-search-bar :radius="100"></uni-search-bar>
		<view class="category_content">
			<scroll-view scroll-y scroll-with-animation enable-back-to-top>
			  <view 
					v-for="(leftNav,index) in leftNavList"
					:key="leftNav"
					@tap="switchCategory(index)"
					:class="[currentIndex == index ? 'left_nav_bar_active':'']">
			  	{{leftNav}}
			  </view>   
			</scroll-view>
			
			<view class="right_content">
				<scroll-view scroll-y scroll-with-animation>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
					<view>{{currentIndex}}</view>
				</scroll-view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				leftNavList: [
					'推荐分类', 
					'极品超市',
					'国际名牌',
					'奢侈品',
					'精品国际',
					'唯品会',
					'男装',
					'女装',
					'男鞋',
					'女鞋',
					'内衣配饰',
					'箱包手袋',
					'美妆护肤',
					'个性清洁',
					'钟表珠宝',
					'电脑办公',
				],
				currentIndex: 0,
				currentCategoryData: [], 
			}
		},
		methods: {
			switchCategory(index) {
				if(this.currentIndex !== index) {
					this.currentIndex = index
					// 切换右侧分类
					this.requestCategoryData()
				}
			},
			requestCategoryData() {
				
			}
		}
	}
</script>

<style lang="less" scoped>
	.category {
		width: 100%;
		height: 100%;
		scroll-view {
			height: 100%;
			::-webkit-scrollbar {
				display: none;
			}
		}
		
		.category_content {
			width: 100%;
			height: calc(~'100% - 54px');
			display: flex;
			& > scroll-view {
				width: 240rpx;
				background-color: #f6f6f6;
				view {
					width: 100%;
					text-align: center;
					height: 80rpx;
					line-height: 80rpx;
				}
			}
			.right_content {
				flex: 1;
				overflow: hidden;
				background-color: #ffffff;
				view {
					height: 20%;
					margin: 0 auto;
				}
			}
			.left_nav_bar_active {
				position: relative;
				background-color: #fff;
				// font-size: 34rpx;
				font-weight: 600;
				&:before {
					content: '';
					width: 8rpx;
					height: 30rpx;
					position: absolute;
					top: 25rpx;
					left: 0;
					background-color: #E41F19;
				}
			}
		}
	}
</style>
