<template>
	<view class="search">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;"></uni-icons>
			<view class="name">搜索</view>
		</view>
		
		<view class="search-box">
			<input placeholder="请输入关键字" :showAction="false" v-model="keyword" @custom="sou"/>
		</view>
		
		<view class="user-box">
			<view class="user-contain" v-for="(item,index) in filteredUser" :key="index">
				<view class="user-list">
					<image :src="item.img"></image>
					<span>{{item.username}}</span>
				</view>
				<view class="btn-box">
					<button type="primary">{{message}}</button>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keyword: '',
				message:'发送消息',
				list:[]
			}
		},
		methods:{
			sou(){
				console.log(111111);
			},
			back(){
				uni.navigateBack({
					url:'../../index.index'
				})
			}
		},
		created(){
			uni.request({
				url:'http://localhost:3000/register/userList',
				data:{},
				success: (res) => {
					// console.log(res.data);
					this.list = res.data;
					console.log(this.list);
				}
			})
		},
		computed:{
			//1.搜索功能，使用filter，return的是一个Boolean，运用match返回。
			//2.同时数据展示的v-for需要给filteredUser，而不是数据的数组。
			filteredUser(){
				return this.list.filter((user) =>{
					return user.username.match(this.keyword);
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.search{
		padding-top: var(--status-bar-height);
		
		.search-box{
			margin-top: 32rpx;
		}
		input{
			width: 90%;
			height: 30px;
			margin: 0 auto !important;
			background-color: #FFFFFF;
			border-radius: 20px;
		}
		.input-placeholder{
			padding-left: 22rpx;
		}
		::v-deep .uni-input-wrapper{
			padding-left: 10px;
		}
		::v-deep .u-search__content{
			margin-left: 20rpx;
			// flex-grow: 0;
			// flex-shrink: 0;
			// flex-basis: 400rpx;
		}
		::v-deep .u-search__content,::v-deep .u-search__content__input{
			background-color: #FFFFFF !important;
		}
		
		.user-box{
			padding: 40rpx;
			.user-contain{
				display: flex;
				justify-content: space-between;
				box-shadow:0px 1px 10px 0px rgba(0,0,0,0.1);
				padding: 20rpx;
				margin-bottom: 20rpx;
			}
			
			.user-list{
				// padding: 40rpx;
				image{
					width: 100rpx;
					height: 100rpx;
					border-radius: 20rpx;
					vertical-align: middle;
				}
				span{
					margin-left: 20rpx;
				}
			}
			
			.btn-box{
				.u-button{
					height: 50px;
				}	
			}
		}
	}
	
	.header{
		width: 100%;
		height: 82rpx;
		// background: $uni-bg-color;
		box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		display: inline-flex;
		// justify-content: space-between;
		// z-index: 2;
		.back{
			font-size: 40rpx;
		}
		.back{
			margin: 20rpx;
		}
		.name{
			margin: 24rpx;
			display: inline-flex;
			justify-content: center;
			align-items: center;
			width: 75%;
		}
	}
</style>