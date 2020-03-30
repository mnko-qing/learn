<template>
	<view class="view">
		<view class="search_filter_area">
			<view class="search_area">
				<uni-search-bar :radius="100" @confirm="search">
				</uni-search-bar>
				<text @click="search">搜索</text>
			</view>
			<view class="filter_area">
				<view @click="search">
					人气 <uni-icons type="arrowup"></uni-icons>
				</view>
				<view @click="search">
					价格 <uni-icons type="arrowup"></uni-icons>
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
						<view v-for="item in filterCategory" :key="item">{{item}}</view>
					</view>	
					<view class="divide-line"></view>
					<view class="title">价格区间</view>
					<view class="drawer_category">
						<view class="input_area">
							<input class="uni-input" type="number" placeholder="最低价" />
							-
							<input class="uni-input" type="number" placeholder="最高价" />
						</view>
						<view v-for="item in filterArea" :key="item">{{item}}</view>
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
				filterArea: ['0-50', '50-100', '100-200']
			}
		},
		onLoad() {
			
		},
		methods: {
			search() {
				
			},
			jumpCategory() {
				
			},
			filters() {
				
			},
			reset() {
				
			},
			confirm() {
				
			}
		}
	}
</script>

<style lang="less">
	page {
		padding-top: 10px;
		background-color: #fff;
		.search_filter_area {
			position: fixed;
			padding: 0 15px;
			width: calc(100% - 30px);
			border-bottom: 1px solid #dcdcdc;
			.search_area {
				display: flex;
				.uni-searchbar,uni-search-bar {
					flex: 1;
				}
				& > text {
					color: #f08a31;
					margin-left: auto;
					line-height: 36px;
					width: 52px;
					text-align: center;
				}
			}
			.filter_area {
				display: flex;
				padding: 15px 0;
				font-size: 14px;
				& > view {
					color: #707072;
					width: 25%;
					text-align: center;
					&:last-child {
						display: flex;
						justify-content: center;
						align-items: center;
					}
				}
				uni-icons {
					color: #707072;
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
			}
		}
	}
</style>
