<template>
	<view>
		<view class="card-list">
			<!-- <uni-grid :column="1" :highlight="true" :showBorder="false"> -->

			<view class="card" v-for="(item, index) in cardList" :index="index" :key="index">
				<view class="box">
					<!-- <uni-icons type="image" :size="30" color="#777" /> -->
					<!-- image src='../../../static/image/111.png',:src需要reqiure-->
					<image class="image" :src="item.imgUrl" mode="aspectFit" @error="imageError($event, index)"></image>
					<text class="text">{{item.name}}</text>
					<text class="text-detail">{{item.brand}} - {{item.size}}</text>
				</view>
			</view>

			<!-- </uni-grid> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cardList: [{
					id: 1,
					name: "玻璃窗set", // 名称
					num: 1, // 数量
					room: 'lo', //房间
					// type: "衣物", //分类
					tag: 'set', // 标签
					state: '状态', //状态
					brand: 'JND', //品牌
					size: 'L码', //尺码
					link:'www',//购买链接

					price: '111', //总价
					date: '111', //购买日期

					fullPayment: '111', //定金全款
					spotPrice: '222', // 现货价
					downPayment: '10', //定金
					downPaymentDate: '111', //定金日期
					downPaymentState: '0', //定金支付状态
					finalPayment: '100', //尾款
					finalPaymentDate: '111', //尾款日期
					finalPaymentState: '0', //尾款支付状态
					postage: '7', //邮费

					remark: '备注', //备注
					imgUrl: require('../../../static/image/lo1.jpeg'),
					imgList: ['../../../static/image/lo1.jpeg', '../../../static/image/111.png'],

				}, {
					id: 2,
					name: "cutejsk", // 名称
					num: 1, // 数量
					room: 'lo', //房间
					// type: "衣物", //分类
					tag: 'set', // 标签
					state: '状态', //状态
					brand: 'cuteQ', //品牌
					size: '2码', //尺码
					link:'www',//购买链接

					price: '111', //总价
					date: '111', //购买日期

					fullPayment: '111', //定金全款
					spotPrice: '222', // 现货价
					downPayment: '10', //定金
					downPaymentDate: '111', //定金日期
					downPaymentState: '0', //定金支付状态
					finalPayment: '100', //尾款
					finalPaymentDate: '111', //尾款日期
					finalPaymentState: '0', //尾款支付状态
					postage: '7', //邮费

					remark: '备注', //备注
					imgUrl: require('../../../static/image/lo2.jpeg'),
					imgList: ['../../../static/image/lo2.jpeg'],
				}, {
					id: 3,
					name: "cutejsk11111111111111111111111111111", // 名称
					num: 1, // 数量
					room: 'lo', //房间
					// type: "衣物", //分类
					tag: 'set', // 标签
					state: '状态', //状态
					brand: 'cuteQ3333333333', //品牌
					size: '2码', //尺码
					link:'www',//购买链接

					price: '111', //总价
					date: '111', //购买日期

					fullPayment: '111', //定金全款
					spotPrice: '222', // 现货价
					downPayment: '10', //定金
					downPaymentDate: '111', //定金日期
					downPaymentState: '0', //定金支付状态
					finalPayment: '100', //尾款
					finalPaymentDate: '111', //尾款日期
					finalPaymentState: '0', //尾款支付状态
					postage: '7', //邮费

					remark: '备注', //备注
					imgUrl: require('../../../static/image/111.png'),
					imgList: ['../../../static/image/111.png'],
				}, {
					id: 4,
					name: "cutejsk", // 名称
					num: 1, // 数量
					room: 'lo', //房间
					// type: "衣物", //分类
					tag: 'set', // 标签
					state: '状态', //状态
					brand: 'cuteQ3333333333', //品牌
					size: '2码', //尺码
					link:'www',//购买链接

					price: '111', //总价
					date: '111', //购买日期

					fullPayment: '111', //定金全款
					spotPrice: '222', // 现货价
					downPayment: '10', //定金
					downPaymentDate: '111', //定金日期
					downPaymentState: '0', //定金支付状态
					finalPayment: '100', //尾款
					finalPaymentDate: '111', //尾款日期
					finalPaymentState: '0', //尾款支付状态
					postage: '7', //邮费

					remark: '备注', //备注
					imgUrl: require('../../../static/image/lo2.jpeg'),
					imgList: ['../../../static/image/lo2.jpeg'],
				}]
			}
		},
		methods: {
			imageError(e, index) {
				console.log(11, e, index)
				console.error('image发生error事件，携带值为' + e.detail.errMsg)
				// this.officeApp[i]['app_list'][index]['icon'] = '/static/image/other/app-icon.png'
			},
		}
	}
</script>

<style lang="scss">
	.card-list {
		display: flex;
		flex-wrap: wrap;
		// padding-left: 2px
		// padding-right: 2px;
		// width: 100%;
	}

	.card {
		box-sizing: border-box;
		width: 250rpx; // 750/3=250rpx
		padding: 12rpx;
	}

	.box {
		// 会自动根据padding和border的值来调整content的值
		box-sizing: border-box;
		// width: 300rpx;
		height: 300rpx;
		// overflow: hidden;
		border-radius: 8rpx;
		padding: 3px;
		box-shadow: #ddd 0px 0px 3px 1px;
		border: 1px solid #ebeef5;
		background-color: #fff;

		image {
			width: 100%;
			height: 200rpx;
			border-radius: 8rpx;
		}

		.text {
			// 溢出显示...
			display: block;
			white-space: nowrap;
			overflow: hidden;
			text-overflow: ellipsis;
		}

		.text-detail {
			// 溢出显示...
			display: block;
			white-space: nowrap;
			overflow: hidden;
			text-overflow: ellipsis;

			color: #666;
			font-size: 8rpx;

		}
	}
</style>
