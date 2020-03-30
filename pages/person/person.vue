<template>
	<view class="person">
		<view class="person_head">
			<image src="/static/person/news.png"></image>
			<image src="/static/person/setting.png"></image>
		</view>
		<view class="person_user margin_bottom_10">
			<image :src="userInfo.avatarUrl" class="avatar"></image>
			<text>{{userInfo.nickName}}</text>
			<view class="note"><!-- 随心所欲不逾矩 -->暂无</view>
			<view class="right right_arrow"></view>
		</view>
		<uni-list>
		  <uni-list-item 
				v-for="item in list"
				:key="item.title"
				:thumb="item.src"
				:title="item.title" 
				:class="{'margin_bottom_10': item.divideLine}">
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {},
				list: [
					{title: '我的钱包',src: '/static/person/money.png'},
					{
						title: '我的优惠卷',
						src: '/static/person/coupon.png', 
						divideLine: true,
					},
					{title: '内容订单',src: '/static/person/content_order.png'},
					{title: '实物订单',src: '/static/person/physical_order.png'},
					{title: '我的课程',src: '/static/person/course.png'},
					{title: '我的考试',src: '/static/person/examination.png'},
					{title: '我的作业',src: '/static/person/work.png'},
					{
						title: '我的收藏',
						src: '/static/person/examination.png',
						divideLine: true,
					},
					{title: '我的班级',src: '/static/person/class.png'},
					{title: '我的活动',src: '/static/person/activity.png'},
					{
						title: '我的任务',
						src: '/static/person/task.png',
						divideLine: true,
					},
					{
						title: '我的会员卡',
						src: '/static/person/vip.png',
						divideLine: true,
					}
				]
			}
		},
		onLoad() {
			uni.getUserInfo({
			  provider: 'weixin',
			  success: res => {
			    this.userInfo = res.userInfo
			  }
			})
		},
		methods: {
		
		}
	}
</script>

<style lang="scss" scoped>
	page {
		.right {
			background-image: url("~@/static/person/right.png");
			background-size: 100% 100%;
		}
		.person > view {
			background-color: #fff;
		}
		.person_head {
			height: 40px;
			padding: 0 15px;
			image {
				width: 25px;
				height: 25px;
				margin-top: 5px;
			}
			image:last-child {
				float: right;
			}
		}
		.person_user {
			height: 180px;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			position: relative;
			.avatar {
				width: 80px;
				height: 80px;
				border-radius: 50%;
			}
			text {
				margin: 10px 0;
				font-size: 20px;
				font-weight: 600;
				color: black;
			}
			.note {
				font-size: 14px;
				color: #adadad;
			}
			.right_arrow {
				position: absolute;
				right: 15px;
				top:50px;
				width: 22px;
				height: 22px;
			}
		}
		uni-list /deep/ .uni-list {
			background-color: #e5e5e5;
			.uni-list-item {
				background-color: #fff;
			}
			.uni-list-item--hover {
				background-color: $uni-bg-color-hover !important;
			}
		}
	}
</style>
