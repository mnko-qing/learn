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
		<view class="person_content">
			<view class="margin_bottom_10">
				<view class="person_content_item">
					<image class="person_icon" src="/static/person/money.png"></image>
					<view class="person_icon_text">我的钱包</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image class="person_icon" src="/static/person/coupon.png"></image>
					<view class="person_icon_text">我的优惠卷</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
			</view>
			<view class="margin_bottom_10">
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/content_order.png"></image>
					<view class="person_icon_text">内容订单</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/physical_order.png"></image>
					<view class="person_icon_text">实物订单</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/course.png"></image>
					<view class="person_icon_text">我的课程</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/examination.png"></image>
					<view class="person_icon_text">我的考试</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/work.png"></image>
					<view class="person_icon_text">我的作业</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/favorite.png"></image>
					<view class="person_icon_text">我的收藏</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
			</view>
			<view class="margin_bottom_10">
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/class.png"></image>
					<view class="person_icon_text">我的班级</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/task.png"></image>
					<view class="person_icon_text">我的任务</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/activity.png"></image>
					<view class="person_icon_text">我的活动</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
			</view>
			<view class="margin_bottom_10">
				<view class="person_content_item">
					<image 
						class="person_icon" 
						src="/static/person/vip.png"></image>
					<view class="person_icon_text">我的会员卡</view>
					<image class="right" src="/static/person/right.png"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {}
			}
		},
		onLoad() {
			uni.getUserInfo({
			  provider: 'weixin',
			  success: res => {
			    this.userInfo = res.userInfo
					console.log(res)
			  }
			})
		},
		methods: {
		
		}
	}
</script>

<style lang="less">
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
		.person_content {
			background-color: #e5e5e5 !important;
			& > view {
				background-color: #fff;
			}
			.person_content_item {
				height: 50px;
				display: flex;
				align-items: center;
				border-bottom: 1px solid #eae7e7;
				padding-right: 15px;
				margin-left: 60px;
				.person_icon {
					width: 30px;
					height: 30px;
					margin-left: -45px;
				}
				.person_icon_text {
					font-size: 16px;
					padding-left: 10px;
				}
				.right {
					width: 26px;
					height: 26px;
					margin-left: auto;
				}
			}
		}
	}
</style>
