<template>
	<view class="cont">
		<view class="header">
			<view class="name">设置</view>
		</view>
		
		<ul class="nameBox">
			<li class="name">
				<image src="../../static/images/96226079_p0_master1200.jpg" mode=""></image>
				<view class="name-message">
					zhanghao
					<p>账号</p>
				</view>
		
			</li>
		</ul>
		
		<ul class="chageBox">
			<li @tap="security()">
				账号与安全
				<uni-icons type="right"></uni-icons>
			</li>
			<li>
				新消息通知
				<uni-icons type="right"></uni-icons>
			</li>
			<li @tap="about()">
				关于
				<uni-icons type="right"></uni-icons>
			</li>
		</ul>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				value:false
			}
		},
		methods:{
			security(){
				uni.navigateTo({
					url:'./security'
				})
			},
			about(){
				uni.navigateTo({
					url:'./contentPage/about'
				})
			}
		},
		change(e){
			console.log(e);
		}
	}
</script>

<style lang="scss" scoped>
	.cont{
		padding-top: var(--status-bar-height);
	}
	.header{
		width: 100%;
		height: 88rpx;
		// background: $uni-bg-color;
		box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		margin-bottom: 30rpx;
		position: relative;
		.name{
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%,-50%);
		}
	}
	.nameBox{
		margin-bottom: 30rpx;
		.name{
			display: flex;
			padding: 20rpx;
			image{
				max-width: 84rpx;
				height: 84rpx;
			}
			.name-message{
				margin-left: 28rpx;
				p{
					font-size: 28rpx;
					margin-top: 5rpx;
					color: #909399;
				}
			}
		}
	}
	.chageBox,.nameBox{
		padding: 20rpx;
		box-shadow:0px 1px 10px 0px rgba(0,0,0,0.1);
	}
	.chageBox{
		li{
			display: flex;
			justify-content: space-between;
			list-style: none;
			padding: 20rpx;
			border-bottom: 1px dashed rgba(0,0,0,0.2);
		}
	}
	.dark-mode{
		filter:invert(1) hue-rotate(180deg);
	}
</style>