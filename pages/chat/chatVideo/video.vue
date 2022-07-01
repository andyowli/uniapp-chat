<template>
	<view class="grad" v-show="cancel">
		<view class="title">
			<span>等待对方连接中...</span>
		</view>
		<view class="imgPhoto">
			<image src="../../../static/images/96226079_p0_master1200.jpg" mode=""></image>
		</view>
		
		<view style="width: 100%;height:52%;"></view>
		<view class="btn">
			<view class="phone" @click="close">
				<image src="../../../static/images/live/phone.png"></image>
			</view>
			<view class="yuyin">
				<image src="../../../static/images/live/yuyin.png" ></image>
			</view>
		</view>
		<view class="btn-title">
			<span>取消</span>
			<span>切换到语音</span>
		</view>
	</view>
</template>

<script>
const innerAudioContext = uni.createInnerAudioContext(); //创建音频对象
export default {
	data(){
		return {
			cancel:true,
		}
	},
	methods:{
		close(){
			this.cancel = false;
			innerAudioContext.stop();
		},
		playVoice() { 
			// const innerAudioContext = uni.createInnerAudioContext();
			// innerAudioContext.autoplay = true; //自动开始播放
			innerAudioContext.play(); 
			innerAudioContext.loop = true; //循环播放
			innerAudioContext.src = require('../../../static/images/live/lingsheng.mp3');
			// innerAudioContext.src = 'https://bjetxgzv.cdn.bspapp.com/VKCEYUGU-hello-uniapp/2cc220e0-c27a-11ea-9dfb-6da8e309e0d8.mp3';
			innerAudioContext.onPlay(() => {
			  console.log('开始播放');
			});
			innerAudioContext.onError((res) => {
			  console.log(res.errMsg);
			  console.log(res.errCode);
			});
		}
	},
	mounted() {
		this.playVoice();
	}
}
</script>

<style lang="scss" scoped>
	.grad{
		width: 100vw;
		height: 100vh;
		position: absolute;
		top: 0;
		left: 0;
		z-index: 20;
		background-image: linear-gradient(#a8a7a9, #ecebec,#a9a8a9);
		padding-top: var(--status-bar-height);
		
		.title{
			text-align: center;
			padding: 20px;
		}
		
		.imgPhoto,image{
			width: 80px;
			height: 80px;
			border-radius: 50%;
			
		}
		.imgPhoto{
			margin: auto;
			margin-top: 10%;
		}
		
		.btn,.btn-title{
			display: flex;
			justify-content: space-around;
			
			.phone{
				background: #ff5252;
			}
			.yuyin{
				background: #99989a;
			}
			.phone,.yuyin{
				border-radius: 50%;
			}
			.phone,.yuyin{
				width: 60px;
				height: 60px;
				display: flex;
				align-items: center;
				justify-content: center;
				flex-direction: column;
			}
			.phone image,.yuyin image{
				width: 40px;
				height: 40px;
			}
		}
		.btn-title span{
			width: 82px;
			text-align: center;
			padding: 10px;
			font-size: 14px;
			color: #edeced;
		}
	}
</style>