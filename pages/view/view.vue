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
			  <view style="padding: 30rpx;">
			    <view class="title">类型</view>
					<view class="drawer_category">
						<text v-for="(item,index) in filterCategory" 
						:key="index">{{item.text}}</text>
					</view>		
					<view class="title">价格区间</view>
					<view class="drawer_category">
						
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
				filterCategory: [
					{text: '全部', type: 1},
					{text: '课程', type: 1},
					{text: '活动', type: 1},
					{text: '商品', type: 1},
					{text: '社群', type: 1},
					{text: '0-50', type: 2},
					{text: '50-100', type: 2},
					{text: '100-200', type: 2},
				],
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
				
			}
		}
	}
</script>

<style lang="less">
	page {
		padding: 10px 0;
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
				.title {
					padding: 20rpx 0;
					font-size: 18px;
				}
				.drawer_category {
					display: flex;
					flex-wrap: wrap;
					& > text {
						background-color: #f0edec;
						color: #767676;
						text-align: center;
						width: 120rpx;
						height: 60rpx;
						line-height: 60rpx;
						border-radius: 50rpx;
						margin: 0 10px 10px 0;
					}
				}
			}
		}
	}
</style>
