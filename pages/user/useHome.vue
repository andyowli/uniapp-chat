<template>
	<view class="box">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;"></uni-icons>
			<view class="more">...</view>
		</view>
		<view class="bg">
			<image src="../../static/images/96226079_p0_master1200.jpg" mode="aspectFill" class="bei"></image>
			<!-- <view class="mask"></view> -->
			<view class="main">
				<view class="tou">
					<image src="../../static/images/96226079_p0_master1200.jpg" mode=""></image>
				</view>
				<view class="text">
					<view class="name">宇文所拓</view>
					<view class="content">
						夜，结束了一天的喧嚣后安静下来，伴随着远处路灯那微弱的光。风，毫无预兆地席卷整片旷野，撩动人的思绪万千。
					</view>
				</view>
				<view class="btn">
					<span>加为好友</span>
				</view>
			</view> 
			<!-- <view class="main">
				<view class="name">宇文所拓</view>
				<view class="content">
					夜，结束了一天的喧嚣后安静下来，伴随着远处路灯那微弱的光。风，毫无预兆地席卷整片旷野，撩动人的思绪万千。
				</view>
			</view> -->
		</view>
	</view>
</template>

<script>
</script>

<style lang="scss" scoped>
	.box{
		width: 100%;
		height: 100%;
		overflow: hidden;
		// display: flex;
		// flex-direction: column;
		// align-items: center;
		// justify-content: center;
		// background-image: url(../../static/images/96226079_p0_master1200.jpg);
		// background-size: 100% 100%;
		// filter: blur(12px);
		// transform: scale(1.2); 
	}
	uni-page-body{
		height: 100%;
	}
	.header{
		width: 100%;
		height: 88rpx;
		// background: $uni-bg-color;
		// box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		display: flex;
		justify-content: space-between;
		z-index: 2;
		.back,.more{
			font-size: 40rpx;
		}
		.back{
			margin: 20rpx;
		}
		.more{
			margin: 10rpx 24rpx 0 0;
		}
	}
	.bg{
		width: 100%;
		height: 100%;
		position: relative;
		z-index: -1;
		.bei{
			width: 100%;
			height: 100%;
			filter: blur(16px);
			transform: scale(1.2); 
		}
		.main{
			width: 100%;
			height: 100%;
			position: absolute;
			top: 4%;
			left: 0;
			right: 0;
			// bottom: 0;
			margin: auto;
			.tou{
				width: 400rpx;
				height: 400rpx;
				border: 6rpx solid #FFFFFF;
				border-radius: 48rpx;
				margin: auto;
				image{
					width: 100%;
					height: 100%;
					border-radius: 40rpx;
				}
			}
			.text{
				text-align:center;
				padding: 60rpx;
				margin: -20rpx 0 0 0;
				.name{
					width: 252rpx;
					height: 74rpx;
					font-family: PingFangSC-Regular;
					font-size: 52rpx;
					color: #272832;
					// letter-spacing: -0.89px;
					font-weight: 400;
					margin: auto;
				}
				.content{
					font-family: PingFangSC-Light;
					font-size: 28rpx;
					color: #272832;
					letter-spacing: -0.96rpx;
					line-height: 48rpx;
					font-weight: 200;
				}
			}
			.btn{
				width: 684rpx;
				height: 80rpx;
				background: #FFE431;
				border-radius: 10rpx;
				margin: auto;
				position: relative;
				span{
					width: 124rpx;
					height: 44rpx;
					font-family: PingFangSC-Regular;
					font-size: 32rpx;
					color: #272832;
					letter-spacing: -1.1rpx;
					font-weight: 400;
					position: absolute;;
					top: 0;
					right: 0;
					bottom: 0;
					left: 0;
					margin: auto;
			
				}
			}
		}
	}
</style>
