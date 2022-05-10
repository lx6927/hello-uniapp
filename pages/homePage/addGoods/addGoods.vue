<template>
	<view class="drawer-view">
		<uni-drawer class="drawer" ref="drawer" mode="right" :width="400" @change="change($event,'drawer')">
			<view class="inner">

				<view class="header">
					<view class="btn-back" @tap="navigateBack">
						<i class="uni-btn-icon" style="color: rgb(0, 0, 0); font-size: 27px;"></i>
					</view>
					<text class="title">添加物品</text>
				</view>


				<uni-forms class="form" ref="form" :modelValue="formData" :rules="rules">
					<!-- 文件 -->
					<uni-card :is-shadow="false" :isFull="true">
						<uni-file-picker ref="files" v-model="imageValue" file-mediatype="image"
							file-extname="png,jpg,jpeg" limit="3" :auto-upload="false" @progress="progress"
							@success="success" @fail="fail" @select="select"></uni-file-picker>
					</uni-card>

					<!-- 类型 -->
					<!-- <uni-card :is-shadow="false"> -->
					<!-- <uni-forms-item label="类型" name="name">
							<uni-easyinput type="text" v-model="formData.name" placeholder="请输入姓名" />
						</uni-forms-item> -->
					<!-- </uni-card> -->

					<!-- 表单 -->
					<uni-card :is-shadow="false" :isFull="true">
						<uni-forms-item label="名称" name="name" required>
							<uni-easyinput type="text" v-model="formData.name" placeholder="" />
						</uni-forms-item>
						<uni-forms-item label="数量" name="num">
							<uni-easyinput v-model="formData.num" placeholder="" />
						</uni-forms-item>
						<uni-forms-item label="房间" name="room" required>
							<uni-easyinput v-model="formData.room" placeholder="" />
						</uni-forms-item>

						<!-- 价格 -->
						<uni-forms-item label="全款" name="fullPayment">
							<uni-easyinput v-model="formData.fullPayment" placeholder="" />
						</uni-forms-item>
						<uni-forms-item label="定金" name="downPayment">
							<uni-easyinput v-model="formData.downPayment" placeholder="" />
						</uni-forms-item>
						<uni-forms-item label="尾款" name="finalPayment">
							<uni-easyinput v-model="formData.finalPayment" placeholder="" />
						</uni-forms-item>




						<uni-forms-item label="备注" name="remark">
							<uni-easyinput type="textarea" v-model="formData.remark" placeholder="" />
						</uni-forms-item>
						<button @click="submitForm">添加物品</button>
					</uni-card>


				</uni-forms>

			</view>
		</uni-drawer>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imageValue: [],
				formData: {
					// id:1,
					name: "玻璃窗set", // 名称
					num: 1, // 数量
					room: 'lo', //房间
					// type: "衣物", //分类
					tag: 'set', // 标签
					state: '状态', //状态
					brand: 'JND', //品牌
					size: 'L码', //尺码
					link: 'www', //购买链接

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
					// imgUrl: require('../../../static/image/lo1.jpeg'),
					imgList: ['../../../static/image/lo1.jpeg', '../../../static/image/111.png'],
				},
				rules: {
					// 对name字段进行必填验证
					name: {
						rules: [{
							required: true,
							errorMessage: '名称不能为空',
						}]
					},
					num: {
						rules: [{
							format: 'number',
							errorMessage: '只能输入数字'
						}]
					},
					room: {
						rules: [{
							required: true,
							errorMessage: '房间不能为空',
						}]
					},
					fullPayment: {
						rules: [{
							format: 'number',
							errorMessage: '只能输入数字'
						}]
					},
					downPayment: {
						rules: [{
							format: 'number',
							errorMessage: '只能输入数字'
						}]
					},
					finalPayment: {
						rules: [{
							format: 'number',
							errorMessage: '只能输入数字'
						}]
					},
				}
			}
		},
		props: ['openStatus'],
		watch: {
			openStatus(newValue, oldValue) {
				console.log(111, newValue, oldValue)
				if (newValue && !oldValue) {
					this.$refs["drawer"].open()
				}

			}
		},
		methods: {
			// 抽屉状态发生变化触发
			change(e, type) {
				console.log(e, type);
			},
			navigateBack() {
				this.$emit('changeOpenStatus', false);
				this.$refs["drawer"].close()
				// uni.navigateBack();
				// uni.navigateTo({
				// 	url: 'pages/tabBar/API/API'
				// })
			},
			// 选择文件后触发
			select() {

			},
			// 文件上传时触发,上传进度,上传文件索引,当前文件对象
			progress(progressm, index, tempFile, tempFiles, tempFilePaths) {
				console.log(110, progressm, index, tempFile, tempFiles, tempFilePaths)
			},
			// 上传成功触发
			success(file) {
				console.log(111, file)
			},
			// 上传失败触发
			fail() {

			},
			// 文件从列表移除时触发
			delete() {

			},
			submitForm() {
				// this.$refs.files.upload()
				// console.log(this.imageValue, this.$refs.files)
				this.$refs["form"].validate().then(res => {
					let data = {

					}
				}).catch(err => {
					console.log('err0', err);
				})
			}
		}
	}
</script>

<style lang="scss">
	.drawer .inner {
		background-color: #f7f7f7;
	}

	.header {
		// background-color: #ddd;
		height: 44px;
		line-height: 44px;
		display: flex;

		.title {
			font-weight: 700;
			font-size: 16px;
		}
	}

	.btn-back {
		width: 60px;
		text-align: center;
		// height: 44px;
		line-height: 55px;
	}

	.drawer-view {
		.form {
			/deep/ .uni-forms-item__inner {
				padding-bottom: 17px;
			}
		}
	}
</style>
