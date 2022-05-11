<template>
	<view>

		<view class="tab_nav">
			<view class="navTitle" v-for="(item,index) in navList" :key="item.index">
				<view :class="{'active':isActive===index}" @click="checked(index)">
					{{item.title}}
				</view>
			</view>
		</view>
		<view class="nav_item" v-if="isActive===0">
			<tabAll></tabAll>
		</view>
		<view class="nav_item" v-if="isActive===1">1</view>
		<view class="nav_item" v-if="isActive===2">2</view>

		<!-- <uni-section title="物品" type="line" padding>
			<uni-grid :column="4" :highlight="true">
				<uni-grid-item v-for="(item, index) in 16" :index="index" :key="index">
					<view class="grid-item-box" style="background-color: #fff;">
						<uni-icons type="image" :size="30" color="#777" />
						<text class="text">文本信息</text>
					</view>
				</uni-grid-item>
			</uni-grid>
		</uni-section> -->

		<uni-fab :pattern="pattern" @fabClick="fabClick"></uni-fab>

		<addGoods :openStatus="openStatus" @changeOpenStatus="changeOpenStatus"></addGoods>

	</view>
</template>

<script>
	import tabAll from './tabAll/tabAll.vue'
	import addGoods from './addGoods/addGoods.vue'

	export default {
		components: {
			tabAll,
			addGoods
		},
		data() {
			return {
				isActive: 0,
				navList: [{
						index: 0,
						title: '全部'
					},
					{
						index: 1,
						title: '物品1'
					},
					{
						index: 2,
						title: '物品2'
					},
				],

				// 悬浮按钮
				pattern: {
					color: '#7A7E83',
					backgroundColor: '#fff',
					selectedColor: '#007AFF',
					buttonColor: '#007AFF',
					iconColor: '#fff'
				},

				// 抽屉
				openStatus: false,
			};
		},
		onReady() {
			setTimeout(()=>{
				this.ajax();

			},5000)
		},
		methods: {
			ajax() {
				this.$Z.get('/article').then(res=>{
					console.log(11111111,res)
				}).catch(err=>{
					console.log(2222,err)
				})
			},
			checked(index) {
				this.isActive = index
			},
			fabClick() {
				// this.$refs["showLeft"].open()
				this.openStatus = true;
				uni.showToast({
					title: '点击了悬浮按钮',
					icon: 'none'
				})
			},
			changeOpenStatus(status){
				this.openStatus = status;
			}

		}
	}
</script>

<style lang="scss">
	.tab_nav {
		display: flex;
		justify-content: flex-start;
		align-items: center;
	}

	.tab_nav .navTitle {
		width: 100rpx;
		height: 40px;
		line-height: 40px;
		// width: 100%;
		text-align: center;
		font-size: 30rpx;
		font-family: Alibaba PuHuTi;
		color: #333;
		// transition: all;
	}

	.active {
		position: relative;
		color: #333;
	}

	.active::after {
		content: "";
		position: absolute;
		width: 95rpx;
		height: 5rpx;
		background-color: #FFC125;
		left: 0px;
		right: 0px;
		bottom: 0px;
		margin: auto;
	}
</style>
