<template>
	<view class="contain">
		<view class="header">
			<uni-icons type="left" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;" @tap="back"></uni-icons>
			<view class="name">设置</view>
		</view>
		<view class="content">
			<ul class="securityCont">
				<li>
					<span>账号</span>
					<span>
						123456
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
				<li>
					<span>手机号</span>
					<span>13678901234</span>
				</li>
			</ul>
			
			<ul class="securityCont">
				<li @tap="alter">
					<span>修改密码</span>
					<span>
						123456
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
				<li @tap="real">
					<span>实名认证</span>
					<span>
						未设置
						<uni-icons type="right" style="font-size: 34rpx;"></uni-icons>
					</span>
				</li>
			</ul>
			
			<ul class="cancellation">
				<li @tap="destroy">
					<span>账号注销</span>
					<span><uni-icons type="right" style="font-size: 34rpx;"></uni-icons></span>
				</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default{
		methods:{
			back(){
				console.log(111111);
				uni.navigateBack({
					url:'../setting'
				})
			},
			alter(){
				uni.navigateTo({
					url:'./contentPage/alterPas'
				})
			},
			destroy(){
				uni.navigateTo({
					url:'./contentPage/destroy'
				})
			},
			real(){
				uni.navigateTo({
					url:'./contentPage/Realname'
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
		.content{
			padding: 30rpx;
			.securityCont,.cancellation{
				font-size: 32rpx;
				padding: 20rpx;
				box-shadow:0px 1px 10px 0px rgba(0,0,0,0.1);
				margin-bottom: 20rpx;
				li{
					list-style: none;
					display: flex;
					justify-content: space-between;
					padding: 20rpx;
				}
			}
			.securityCont{
				li{
					border-bottom: 1px dashed rgba(0,0,0,0.2);
				}
			}
		}
	}
</style>
