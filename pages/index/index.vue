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
        <view>
          <image :src="'/static/category/' + item.imageName + '.png'"></image>
        </view>
        <text>{{item.text}}</text>
      </view>
		</view>
		<view class="list">
      <view class="margin_bottom_10" v-for="(item,index) in list" :key="index">
        <view class="title">{{item.title}}</view>
        <view 
          class="list_item" 
          :class="{'margin_bottom_10': subIndex === item.list - 1}"
          v-for="(sub, subIndex) in item.list" 
          :key="sub.studyNum">
          <image :src="sub.image"></image>
          <text v-if="sub.type == 'text'">图文</text>
          <text v-else-if="sub.type == 'audio'">音频</text>
          <text v-else>视频</text>
          <view class="list_item_title">{{sub.title}}</view>
          <view class="list_item_info">
            <text v-if="sub.period == 1">单品</text>
            <text v-else>共{{sub.period}}期</text>
            <text style="padding-left: 5px;">| {{sub.studyNum}}学习</text>
            <text v-if="sub.free" class="free">免费</text>
          </view>
        </view>
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
            list: [{
              image: '/static/banner/banner_1.png',
              type: 'text',
              free: true,
              period: 1,
              title: '专享升级:2020春节活动',
              studyNum: 10973
            }, {
              image: '/static/banner/banner_1.png',
              type: 'audio',
              free: true,
              period: 11,
              title: '喜讯:2020老子学院开课啦',
              studyNum: 1098
            }, {
              image: '/static/banner/banner_1.png',
              type: 'vedio',
              free: true,
              period: 10,
              title: '武当仙山上的守护者',
              studyNum: 11182
            }]
					}, {
            title: '问道系列',
            list: [{
              image: '/static/banner/banner_1.png',
              type: 'vedio',
              free: true,
              period: 10,
              title: '[问道系列] 健康长生',
              studyNum: 209
            }, {
              image: '/static/banner/banner_1.png',
              type: 'vedio',
              free: true,
              period: 10,
              title: '[问道系列] 未来教育',
              studyNum: 209
            }]
          }, {
            title: '冥想',
            list: [{
              image: '/static/banner/banner_1.png',
              type: 'audio',
              free: true,
              period: 15,
              title: '[冥想] 创造全新的自己',
              studyNum: 20085
            }, {
              image: '/static/banner/banner_1.png',
              type: 'audio',
              free: true,
              period: 6,
              title: '[冥想] 恩典',
              studyNum: 12486
            }]
          },
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
			height: 400rpx;
			width: 100%;
			image {
				width: 100%;
				height: 100%;
			}
		}
		.category {
			display: grid;
      padding: 15px;
      grid-gap: 20rpx;
      grid-template-columns: repeat(4, 1fr);
      grid-template-rows: repeat(2, 1fr);
      .category_item {
        padding: 20rpx;
        height: 150rpx;
        & > view {
          height: 100rpx;
          border-radius: 12px;
          border: 1px solid #C0C0C0;
          box-shadow: 0 3px 1px 0px #eee9e9;
          display: flex;
          justify-content: center;
          align-items:center;
        }
        image {
        	width: 80rpx;
        	height: 80rpx;
        }
        text {
          color: #555456;
          font-size: 26rpx;
          text-align: center;
          display: block;
          width: 100%;
          padding-top: 10px;
        }
      }
		}
		.list {
      background-color: #e5e5e5;
      & > view {
        padding: 15px;
        background-color: #fff;
      }
      .title {
        text-align: center;
        font-size: 20px;
        font-weight: 600;
        padding-bottom: 10px;
        &:after {
          content: '';
          display: block;
          background-color: #C8C7CC;
          width: 40px;
          height: 4px;
          margin: 5px auto;
          border-radius: 4px;
        }
      }
      .list_item {
        position: relative;
        & > text {
          position: absolute;
          top: 90px;
          right: 10px;
          width: 50px;
          height: 22px;
          border-radius: 8px;
          background-color: rgba(122, 122, 122, 0.5);
          text-align: center;
          color: #fff;
          font-size: 14px;
        }
        .list_item_title {
          font-size: 16px;
          padding: 10px 0;
          width: 100%;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
        }
        .list_item_info {
          display: flex;
          color: #c1c1c1;
          padding-bottom: 10px;
          .free {
            margin-left: auto;
            color: #f33e54;
          }
        }
        image {
        	height: 120px;
        	width: 100%;
        	border-radius: 4px;
        }
      }
		}
	}
</style>
