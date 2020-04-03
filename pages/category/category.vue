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
			<block v-for="(leftNav,index) in leftNavList" :key='leftNav'>
				<scroll-view scroll-y>
				    
				</scroll-view>
			</block>
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
			}
		},
		methods: {
			switchCategory(index) {
				if(this.currentIndex !== index) {
					this.currentIndex = index
					// 切换右侧分类
				}
			}
		}
	}
</script>

<style lang="less" scoped>
	.category {
		width: 100%;
		height: 100%;
		.category_content {
			width: 100%;
			height: calc(~'100% - 54px');
			// border-top: 1px solid #E0E0E0;
			display: flex;
			scroll-view {
				height: 100%;
				::-webkit-scrollbar {
					/* 隐藏滚动条，但依旧具备可以滚动的功能 */
					display: none
				}
				&:first-child {
					width: 240rpx;
					background-color: #f6f6f6;
					view {
						width: 100%;
						text-align: center;
						height: 80rpx;
						line-height: 80rpx;
					}
				}
				&:last-child {
					flex: 1;
					background-color: #ffffff;
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
