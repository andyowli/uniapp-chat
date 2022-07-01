<template>
	<view class="">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;z-index: 1;"></uni-icons>
			<view class="more">...</view>
			<view class="bg">
				<image src="../../static/images/96226079_p0_master1200.jpg" class="bg-img"></image>
			</view>
		</view>
		<view class="main">
			<view class="main-inner">
				<view class="inf">
					<view class="mes-group">
						<view class="name">天气不错</view>
						<view class="tiem">2020-12-1</view>
					</view>
					<view class="notice">上了看得见风景二十九</view>
				</view>
				<view class="member">
					<view class="top">
						<view class="title">群成员</view>
						<view class="mang">
							<view class="manage">管理群成员</view>
							<uni-icons type="right" class="mang-img"></uni-icons>
						</view>
					</view>
					<view class="user-img-list">
						<view class="user-img">
							<image src="../../static/zhaopian.png" mode=""></image>
							<view class="">111</view>
						</view>
						<view class="user-img">
							<image src="../../static/zhaopian.png" mode=""></image>
						</view>
						<view class="user-img">
							<image src="../../static/zhaopian.png" mode=""></image>
						</view>
						<view class="user-img">
							<image src="../../static/zhaopian.png" mode=""></image>
						</view>
						<view class="user-img">
							<image src="../../static/zhaopian.png" mode=""></image>
						</view>
					</view>
				</view>
			</view>
			
			<ul class="securityCont">
				<li>
					<span>群名称</span>
					<span>
						夏天的家族
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
				<li>
					<span >群公告</span>
					<span>
						未设置
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
				<li>
					<span>群内名称</span>
					<span>
						夏天的秋蝉
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
			</ul>
			<view class="button">
				退出群聊
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style lang="scss" scoped>
	.header{
		width: 100%;
		height: 88rpx;
		// background: $uni-bg-color;
		// box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		// margin-bottom: 30rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.more{
			height: 100%;
			font-size: 26px;
			margin-right: 19px;
			z-index: 1;
		}
	}
	.bg{
		width: 100%;
		height: 100%;
		background: #fff;
		position: fixed;
		top: 0;
		left: 0;
		// z-index: -1;
		.bg-img{
			width: 100%;
			height: 750rpx;
		}
	}
	.main{
		position: relative;
		padding-top: 360rpx;
		.main-inner{
			width: 100%;
			background: #fff;
			border-radius: 40rpx 40rpx 0 0;
		}
		.inf{
			padding: $uni-spacing-row-base $uni-spacing-col-base 0;
			border-bottom:1px solid #eee;
		}
		.mes-group{
			display: flex;
			justify-content: space-between;
		}
		.notice{
			padding-top: 20rpx;
			font-size: 20rpx;
			color: #272832;
			line-height: 40rpx;
			overflow: hidden;
		}
		.member{
			border-bottom:1px solid #eee;
			.top{
				width: 100%;
				display: flex;
				justify-content: space-between;
				padding: 28rpx 64rpx 0;
				.title{
					// flex: 1;
					font-weight: 600;
					font-size: 36rpx;
					color: #272832;
				}
				.mang{
					width: 100px;
					display: flex;
					justify-content: space-between;
					.manage{
						color: rgba(39, 40, 50, 0.6);
						font-weight: 400;
						font-size: 32rpx;
					}
					.mang-img{
						line-height: 48rpx;
					}
				}
			}
			.user-img-list{
				display: flex;
				justify-content: space-between;
				padding: 28rpx 64rpx 0;
				.user-img{
					width: 50px;
					height: 80px;
					text-align: center;
					image{
						width: 50px;
						height: 50px;
					}
				}
			}
		}
		.securityCont{
			font-size: 32rpx;
			padding: 20rpx;
			li{
				list-style: none;
				display: flex;
				justify-content: space-between;
				padding: 40rpx;
				border-bottom: 1px dashed rgba(0,0,0,0.2);
			}
		}
		.button{
			width: 100%;
			height: 88rpx;
			background: #eee;
			display: flex;
			justify-content: center;
			align-items: center;
			color: $uni-color-warning;
		}
	}
</style>