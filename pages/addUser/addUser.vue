<template>
	<view class="contain">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;"></uni-icons>
			<view class="name">好友申请</view> 
		</view>
		
		<view class="main">
			<view class="requester">
				<view class="reques-top">
					<view class="reject btn">拒绝</view>
					<view class="head-img">
						<image src="../../static/images/96226079_p0_master1200.jpg"></image>
					</view>
					<view class="aggree btn">同意</view>
				</view>
				<view class="reques-center">
					<view class="title">夏天的柠檬</view>
					<view class="time">2022-4-25</view>
				</view>
				<view class="notic">
					<text>留言:</text>
					你好，我是夏天的柠檬。111111111111111111111111111111111111111111111
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		methods:{
			back(){
				uni.navigateBack({
					url:'../../index/index'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.contain{
		padding-top: var(--status-bar-height);
		.header{
			width: 100%;
			height: 88rpx;
			// background: $uni-bg-color;
			box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
			margin-bottom: 30rpx;
			position: relative;
			.name{
				font-size: 30rpx;
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%,-50%);
			}
		}
		.main{
			padding: 20px;
			.requester{
				padding: 20rpx;
				background: rgba(255, 255, 255, 1);
				box-shadow: 0px 24rpx 64rpx -8rpx rgba(0, 0, 0, 0.1);
				border-radius: 20px;
				.reques-top{
					display: flex;
					flex-direction: row;
					.btn{
						// flex: none;
						width: 160rpx;
						height: 64rpx;
						background: rgba(255, 93, 91, 0.1);
						border-radius: 40rpx;
						font-size: 32rpx;
						line-height: 32px;
						text-align: center;
					}
					.reject{
						background: rgba(255, 93, 91, 0.1);
						color: $uni-color-warning;
					}
					.aggree{
						background: $uni-color-success;
						color: $uni-text-color;
					}
					.head-img{
						margin-top: -72rpx;
						flex: auto;
						text-align: center;
						image{
							width: 144rpx;
							height: 144rpx;
							border-radius: 50%;
						}
						
					}
				}
				.reques-center{
					text-align: center;
					padding-bottom: 40rpx;
					.title{
						font-size: 36rpx;
						font-weight: 400;
						color: $uni-text-color;
						line-height: 50rpx;
					}
					.time{
						font-size: $uni-font-size-sm;
						color: $uni-text-color-disable;
						line-height: 34rpx;
					}
				}
				.notic{
					padding: 20rpx $uni-spacing-col-base;
					font-size: $uni-font-size-base;
					color: $uni-text-color;
					line-height: 40rpx;
					border-radius: $uni-border-radius-base;
					background:$uni-bg-color-grey;
					overflow: hidden;
					word-wrap: break-word;
					word-break: normal;
				}
			} 
		}
	}
</style>