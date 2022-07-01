<template>
	<view class="about-contion">
		<view class="main">
			<view class="main-logo">
				<image src="../../../static/icon/liaotian.png"></image>
				<span>Talkie</span>
			</view>
			<view class="ver">
				<span>Version 1.0.1</span>
			</view>
		</view>
		
	</view>
</template>

<script>
</script>

<style lang="scss" scoped>
	.about-contion{
		.main{
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%,-50%);
			.main-logo{
				
				image{
					width: 160rpx;
					height: 160rpx;
					
				}
				span{
					font-size: 28px;
				}
				image,span{
					vertical-align: middle;
				}
			}
			.ver{
				text-align: center;
				span{
					font-size: 28px;
					font-weight: 500;
				}
			}
		}
	}
</style>