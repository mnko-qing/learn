<template>
	<view class="home">
		<view class="home_header">
			<image src="/static/logo.png"></image>
			<view class="title">
				<text>问道</text>
				<text>\n {{attentionNumber}}关注</text>
			</view>
			<view 
				class="attention" 
				:class="{'attentioned': isAttention}"
				@click="attentionSwtich">
				<text v-if="isAttention">已</text>
				<text v-else>+</text>
				关注
			</view>
		</view>
		<swiper :autoplay="true" :interval="2000" :duration="500">
			<swiper-item>
				<image src="/static/banner/banner_1.png"></image>
			</swiper-item>
			<swiper-item>
				<image src="/static/banner/banner_2.png"></image>
			</swiper-item>
			<swiper-item>
				<image src="/static/banner/banner_3.png"></image>
			</swiper-item>
		</swiper>
		<view class="category margin_bottom_10">
			<view 
				class="category_item" 
				v-for="(item,index) in categorys"
				:key="index">
				<button>
					<image :src="'/static/category/' + item.imageName + '.png'"></image>
				</button>
				<view>{{item.text}}</view>
			</view>
		</view>
		<view class="list margin_bottom_10">
			<view class="title">学院动态</view>
			<view class="">
				<image src="/static/banner/banner_1.png"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isAttention: false,
				attentionNumber: 13265,
				categorys: [
					{imageName: 'course', text: '最新课程'},
					{imageName: 'audio', text: '精彩音频'},
					{imageName: 'video', text: '精彩视频'},
					{imageName: 'category', text: '课程类别'},
					{imageName: 'college', text: '学院动态'},
					{imageName: 'live', text: '直播中心'},
					{imageName: 'commodity', text: '实物商品'},
					{imageName: 'myCourse', text: '我的课程'},
				],
				list: [
					{
						title: '学院动态',
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			attentionSwtich() {
				this.isAttention = !this.isAttention
				this.attentionNumber = this.attentionNumber + (
					this.isAttention ? 1 : -1)
			}
		}
	}
</script>

<style lang="less" scoped>
	.home {
		& > view {
			background-color: #fff;
		}
		.home_header {
			display: flex;
			align-items: center;
			height: 50px;
			padding: 5px 15px;
			font-size: 16px;
			.title {
				padding-left: 15px;
				& text:last-child  {
					font-size: 14px;
					color: #8b8a8f;
				}
			}
			image {
				width: 40px;
				height: 40px;
			}
			.attention{
				margin-left: auto;
				border: 1px solid #f33e54;
				color: #f33e54;
				width: 70px;
				height: 35px;
				line-height: 35px;
				text-align: center;
				border-radius: 50px;
			}
			.attentioned {
				border: 1px solid #7a7070;
				color: #7a7070;
			}
		}
		swiper {
			height: 220px;
			width: 100%;
			image {
				width: 100%;
				height: 100%;
			}
		}
		.category {
			display: flex;
			justify-content: center;
			align-items: center;
			flex-wrap: wrap;
			.category_item{
				width: 25%;
				padding-top: 15px;
				view {
					font-size: 14px;
					width: 100%;
					text-align: center;
					line-height: 3;
				}
				button {
					width: 60px;
					height: 55px;
					border-radius: 12px;
					box-shadow: 0 3px 1px 0px #eee9e9;
					image {
						width: 50px;
						height: 50px;
						margin-left: -8px;
					}
					&::after {
						border: none;
					}
				}
			}
		}
		.list {
			padding: 15px;
			image {
				height: 120px;
				width: 100%;
				border-radius: 4px;
			}
		}
	}
</style>
