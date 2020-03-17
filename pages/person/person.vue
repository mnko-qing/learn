<template>
	<view class="person">
		<view class="person_head">
			<image src="../../static/person/news.png"></image>
			<image src="../../static/person/setting.png"></image>
		</view>
		<view class="person_user margin_bottom_10">
			<image :src="userInfo.avatarUrl" class="avatar"></image>
			<text>{{userInfo.nickName}}</text>
			<view class="note">随心所欲不逾矩</view>
			<view class="right right_arrow"></view>
		</view>
		<view class="person_content margin_bottom_10"></view>
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
			  }
			})
		},
		methods: {
		
		}
	}
</script>

<style lang="less">
	page {
		background-color: #e5e5e5;
		.right {
			background-image: url("~@/static/person/right.png");
			background-size: 100% 100%;
		}
		.margin_bottom_10 {
			margin-bottom: 10px;
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
			height: 200px;
		}
	}
</style>
