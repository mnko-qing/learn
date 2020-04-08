<template>
	<view class="category">
		<uni-search-bar :radius="100"></uni-search-bar>
		<view class="category_content">
			<scroll-view 
				scroll-y 
				enable-back-to-top
				scroll-with-animation
				:scroll-top="scroll.scrollTop">
			  <view 
					v-for="(leftNav,index) in leftNavList"
					:key="leftNav"
					@tap="switchCategory($event,index)"
					:class="[currentIndex == index ? 'left_nav_bar_active':'']">
			  	{{leftNav}}
			  </view>   
			</scroll-view>
			
			<view class="right_content">
				<scroll-view 
          scroll-y 
          enable-back-to-top
          scroll-with-animation
          :scroll-top="scroll.rightScroll">
					<swiper 
						:autoplay="true" 
						:interval="3000" 
						:duration="1000"
						v-if="currentCategoryData.swiper">
						<swiper-item v-for="item in currentCategoryData.swiper" :key="item">
							<image :src="item"></image>
						</swiper-item>
					</swiper>
					<image 
						class="category_banner"
						v-if="currentCategoryData.banner" 
						:src="currentCategoryData.banner">
					</image>
          <view
            class="category_product"
            v-for="item in currentCategoryData.sub"
            :key="item.title">
            <view class="category_product_title">{{item.title}}</view>
            <view class="category_product_wrapper">
              <view 
                v-for="procduct in item.children"
                :key="procduct.name">
                <image :src="procduct.src"></image>
                <view v-if="procduct.name">{{procduct.name}}</view>
              </view>
            </view>
          </view>
				</scroll-view>
			</view>
		</view>
	</view>
</template>

<script>
	import procducts from './category_config_data.js'
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
				scroll: {
					boxHeight: 0,
					scrollTop: 0,
          rightScroll: 0
				},
				loadingCategory: true,
				currentIndex: 0,
				currentCategoryData: {}, 
			}
		},
		mounted() {
			const query = uni.createSelectorQuery().in(this)
			query.select('.category_content').boundingClientRect(data => {
				this.scroll.boxHeight = data.height
			}).exec()
			
			setTimeout( () => {
				this.currentCategoryData = procducts[0]
			},500)
		},
		methods: {
			switchCategory(event,index) {
				if(this.currentIndex !== index) {
					this.currentIndex = index
					
					const offsetTop = event.currentTarget.offsetTop
					const cellHeight = offsetTop / index
					
					let middle = this.scroll.boxHeight / 2
					this.scroll.scrollTop = Math.ceil((offsetTop - middle) / cellHeight) * cellHeight
					this.requestCategoryData(index)
				}
			},
      scrolltoupper() {
        this.currentCategoryData = procducts[this.currentIndex - 1] || []
      },
      scrolltolower() {
        this.currentCategoryData = procducts[this.currentIndex + 1] || []
      },
			requestCategoryData(index) {
        this.scroll.rightScroll = 0
				setTimeout( () => {
					this.currentCategoryData = procducts[index] || []
				},500)
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
			height: calc(~'100% - 52px');
			display: flex;
			& > scroll-view {
				width: 240rpx;
				background-color: #f6f6f6;
				view {
					width: 100%;
					text-align: center;
					height: 100rpx;
					line-height: 100rpx;
          color: #6b6b6b;
				}
			}
			.right_content {
				flex: 1;
				overflow: hidden;
				background-color: #ffffff;
				padding-left: 40rpx;
				padding-right: 20rpx;
				swiper {
					width: 100%;
					height: 220rpx;
				}
				.category_banner {
					height: 200rpx;
				}
        .category_product {
          margin-top: 20rpx;
          width: 100%;
          .category_product_title {
            padding: 20rpx 0;
            font-size: 26rpx;
            color: #000;
          }
          .category_product_wrapper {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            margin: 20rpx 0;
            & > view {
              height: 160rpx;
              display: flex;
              flex-direction: column;
              justify-content: center;
              align-items: center;
              image {
                height: 100rpx;
                width: 100rpx;
              }
              view {
                font-size: 24rpx;
                padding-top: 20rpx;
              }
            }
          }
        }
			}
			.right_content_loading {
				position: relative;
			}
			.left_nav_bar_active {
        color: #000;
				position: relative;
				background-color: #fff;
				font-weight: 600;
				&:before {
					content: '';
					width: 8rpx;
					height: 30rpx;
					position: absolute;
					top: 35rpx;
					left: 0;
					background-color: #E41F19;
				}
			}
		}
	}
</style>
