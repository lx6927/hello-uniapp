<template>
	<view class="personalPage">
		<el-card class="user-card" :is-shadow="false" :isFull="true">
			<view class="user-info">
				<text class="user-name">用户名</text>
				<text class="user">email</text>
			</view>
			<view>
				<image class="user-head" :src="imgUrl"></image>
			</view>
		</el-card>

		<view class="title">
			<text>其他</text>
		</view>

		<view class="uni-panel-c">
			<view class="uni-navigate-item">
				<text class="uni-navigate-text">修改密码</text>
				<text class="uni-navigate-icon uni-icon">&#xe470;</text>
			</view>
			<view class="uni-navigate-item">
				<text class="uni-navigate-text">退出登陆</text>
				<text class="uni-navigate-icon uni-icon">&#xe470;</text>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgUrl: require('../../static/image/lo1.jpeg'),
			}
		},
		mounted() {},
		methods: {}
	}
</script>

<style lang="scss">
	@import '../../common/uni-nvue.css';

	.personalPage {
		padding: 2px 10px;
	}

	.user-card {
		display: flex;
		justify-content: space-between;
		background-color: #fff;
		padding: 10px 15px;
	}

	.user-info {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;

		.user-name {
			font-size: 20px;
			margin-top:15px;
		}
	}

	.user-head {
		width: 200rpx;
		height: 200rpx;
		border-radius: 50%;
	}

	.title {
		font-size: 12px;
		color: #7a7e83;
		margin: 8px 0 3px 0;
	}
</style>
