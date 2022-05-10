<template>
	<view class="loginPage">
		<uni-forms class="form" ref="form" :modelValue="formData" :rules="rules">
			<uni-forms-item label="账号" name="account" required>
				<uni-easyinput type="text" v-model="formData.account" placeholder="请输入账号" />
			</uni-forms-item>
			<uni-forms-item label="密码" name="pwd">
				<uni-easyinput v-model="formData.pwd" placeholder="请输入密码" />
			</uni-forms-item>
			<button type="primary" @click="submit('form')">登陆</button>
		</uni-forms>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				formData: {
					account: "",
					pwd: ""
				},
				rules: {
					// 对name字段进行必填验证
					account: {
						rules: [{
							required: true,
							errorMessage: '账号不能为空',
						}, ]
					},
					pwd: {
						rules: [{
								required: true,
								errorMessage: '密码不能为空',
							},
							{
								minLength: 3,
								maxLength: 12,
								errorMessage: '密码长度在 {minLength} 到 {maxLength} 个字符',
							}
						]
					},
				}
			}
		},
		methods: {
			submit(ref) {
				this.$refs[ref].validate().then(res => {
					let data = {
						account: this.formData.account,
						pwd: this.formData.pwd
					}
					uni.request({
						url: 'http://119.3.132.242/api/login',
						data: data,
						method: 'post',
						// header: {
						// 'custom-header': 'hello' //自定义请求头信息
						// },
						success: (res) => {
							console.log('success', res);
							uni.showToast({
								title: `登陆成功`
							})
							uni.switchTab({
								url: '/pages/homePage/homePage',
							})
						},
						fail: (res) => {
							console.log(res);
							console.log('err', err);
							uni.showToast({
								title: `登陆失败`
							})
						},
					});

				}).catch(err => {
					console.log('err0', err);
				})
			},
			login() {
				let data = {
					account: this.formData.account,
					pwd: this.formData.pwd
				}



				uni.request({
					url: 'http://127.0.0.1:9999/login', //仅为示例，并非真实接口地址。
					data: data,
					method: 'post',
					// header: {
					// 'custom-header': 'hello' //自定义请求头信息
					// },
					success: (res) => {
						console.log(res);
						// this.text = 'request success';
					}
				});
			}
		}
	}
</script>

<style lang="scss">
	.loginPage {
		background-color: #efeff4;
	}

	.form {
		margin: 20px;
	}
</style>
