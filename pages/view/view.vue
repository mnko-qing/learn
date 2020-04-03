<template>
	<view class="view">
		<view class="search_filter_area">
			<view class="search_area">
				<uni-search-bar :radius="100" @confirm="search">
				</uni-search-bar>
				<text @click="search">搜索</text>
			</view>
			<view class="filter_area">
				<view 
					:class="{'filter_type_active': currentSortType == 1}" 
					@click="popularitySort">
					<text>人气</text>
					<view>
						<uni-icons
							type="arrowup"
							:color="currentSortType ==1 ? '#f39b1f' : '#707072'"
							v-if="popularitySortType != 2">
						</uni-icons>
						<uni-icons 
							type="arrowdown"
							:color="currentSortType ==1 ? '#f39b1f' : '#707072'"
							v-if="popularitySortType != 1">
						</uni-icons>
					</view>
				</view>
				<view 
					:class="{'filter_type_active': currentSortType == 2}" 
					@click="priceSort">
					<text>价格</text>
					<view>
						<uni-icons 
							type="arrowup" 
							v-if="priceSortType != 2"
							:color="currentSortType ==2 ? '#f39b1f' : '#707072'">
						</uni-icons>
						<uni-icons 
							type="arrowdown" 
							v-if="priceSortType != 1"
							:color="currentSortType ==2 ? '#f39b1f' : '#707072'">
						</uni-icons>
					</view>
				</view>
				<view @click="jumpCategory">分类</view>
				<view @click="isShowFilters = true">
					筛选<image src="/static/filter.png"></image>
				</view>
			</view>
			<uni-drawer 
				mode="right"
				@close="isShowFilters = false"
				:visible="isShowFilters">
			  <view>
			    <view class="title">类型</view>
					<view class="drawer_category">
						<view 
							@click="setCurrentFilterType(index)"
							v-for="(item,index) in filterCategory" 
							:key="item"
							:class="{'drawer_type_active': currentFilterType == index}">
							{{item}}
						</view>
					</view>	
					<view class="divide-line"></view>
					<view class="title">价格区间</view>
					<view class="drawer_category">
						<view class="input_area">
							<input 
								type="number" 
								@focus="resetFilterPrice" 
								:value="filterAreaToLow"
								placeholder="最低价" />
							-
							<input 
								type="number" 
								@focus="resetFilterPrice" 
								:value="filterAreaToHight"
								placeholder="最高价" />
						</view>
						<view 
							@click="setCurrentFilterPrice(index)"
							v-for="(item,index) in filterArea" 
							:key="item"
							:class="{'drawer_type_active': currentFilterPrice == index}">
							{{item}}
						</view>
					</view>
					<view class="divide-line"></view>
					<view class="drawer_button">
						<view @click="reset">重置</view>
						<view @click="confirm">确定</view>
					</view>
			  </view>
			</uni-drawer>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isShowFilters: false,
				filterCategory: ['全部', '课程', '活动', '商品', '社群'],
				filterArea: ['0-50', '50-100', '100-200'],
				currentFilterType: -1,
				currentFilterPrice: -1,
				filterAreaToLow: '',
				filterAreaToHight: '',
				popularitySortType: 0, //0 默认 1升序 2降序
				priceSortType: 0, //0 默认 1升序 2降序
				currentSortType: 0, //当前排序类型: 1 人气 2价格
			}
		},
		onLoad() {
			
		},
		methods: {
			search() {
				
			},
			jumpCategory() {
				uni.navigateTo({
				    url: '../category/category'
				})
			},
			filters() {
				
			},
			popularitySort() {
				this.currentSortType = 1
				this.popularitySortType == 2 ? 
					this.popularitySortType -- :
					this.popularitySortType ++
				this.search()
			},
			priceSort() {
				this.currentSortType = 2
				this.priceSortType == 2 ? 
					this.priceSortType -- :
					this.priceSortType ++
				this.search()
			},
			reset() {
				this.filterAreaToLow = ''
				this.filterAreaToHight = ''
				this.currentFilterType = -1
				this.resetFilterPrice()
			},
			resetFilterPrice() {
				this.currentFilterPrice = -1
			},
			confirm() {
				this.isShowFilters = false
			},
			setCurrentFilterType(index) {
				this.currentFilterType = index
			},
			setCurrentFilterPrice(index) {
				this.currentFilterPrice = index
			}
		}
	}
</script>

<style lang="less">
	page {
		background-color: #fff;
		.search_filter_area {
			position: fixed;
			padding: 0 15px;
			width: calc(100% - 30px);
			border-bottom: 1px solid #dcdcdc;
			.search_area {
				display: flex;
				justify-content: center;
				align-items: center;
				.uni-searchbar,uni-search-bar {
					flex: 1;
				}
				& > text {
					width: 52px;
					color: #f08a31;
					text-align: center;
				}
			}
			.filter_area {
				display: flex;
				font-size: 14px;
				height: 80rpx;
				& > view {
					color: #707072;
					display: flex;
					flex: 1;
					justify-content: center;
					align-items: center;
					& > view {
						display: flex;
						flex-direction: column;
						justify-content: center;
						align-items: center;
						transform: scale(0.8);
					}
				}
				.filter_type_active {
					color: #f39b1f;
				}
				image {
					width: 16px;
					height: 16px;
				}
			}
			.uni-drawer,uni-drawer {
        & > view {
          padding: 30rpx;
        }
				.title {
					margin: 20rpx 0;
					font-size: 18px;
				}
				.divide-line {
					width: 100%;
					height: 1px;
					background-color: #C8C7CC;
					margin: 20px 0;
				}
				.drawer_category {
					display: grid;
					text-align: center;
					grid-gap: 20rpx;
					grid-template-columns: repeat(3, 1fr);
					grid-template-rows: repeat(2, 1fr);
					& > view {
						background-color: #f0edec;
						border: 1px solid #f0edec;
						color: #767676;
						height: 60rpx;
						line-height: 60rpx;
						border-radius: 50rpx;
					}
					.input_area {
						grid-column-start: span 3;
						background-color: none;
						display: flex;
            justify-content: center;
            align-items: center;
					}
				}
				.drawer_button {
					color: #fff;
					position: absolute;
					bottom: 20px;
					right: 30rpx;
					border-radius: 50px;
					display: flex;
					overflow: hidden;
					& > view {
						width: 140rpx;
						height: 60rpx;
						text-align: center;
						line-height: 60rpx;
						&:first-child {
							border: 1px solid #f39b1f;
							background-color: #f39b1f;
						}
						&:last-child {
							border: 1px solid #f33e54;
							background-color: #f33e54;
						}
					}
				}
				.drawer_type_active {
					color: #fff !important;
					border: 1px solid #f39b1f !important;
					background-color: #feb50b  !important;
				}
			}
		}
	}
</style>
