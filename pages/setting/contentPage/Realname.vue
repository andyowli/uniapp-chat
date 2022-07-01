<template>
	<view>
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;position: absolute;top: 50%;left: 5%;transform: translate(-50%,-50%);"></uni-icons>
			<view class="name">修改密码</view>
		</view>
		
		<view class="input-cont">
			<view class="inputWrite">
				<input type="text" placeholder="请填写您的真实名称" v-model="name"/>
				<input type="number" placeholder="请填写省份证号" v-model="number"/>
			</view>
		</view>
		
		<view class="btn">
			<button type="primary">提交</button>
		</view>
	</view>
</template>

<script>
export default {
	data(){
		return{
			disabled:true,
			name:'' , //姓名
			number:'' //身份证
		}
	},
	methods:{
		back(){
			uni.navigateBack({
				url:'./setting/security'
			})
		}
	}
}
</script>

<style lang="scss" scoped>
	.header{
		width: 100%;
		height: 88rpx;
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
	.input-cont{
		padding: 20rpx;
		.inputWrite{
			padding: 12rpx;
			border-radius: 10rpx;
			box-shadow:0px 1px 10px 0px rgba(0,0,0,0.1);
			input{
				padding: 20rpx;
				border-bottom: 1px dashed rgba(0,0,0,0.2);
			}
		}
	}
	.btn{
		width: 40%;
		padding: 20rpx;
		margin: auto;
	}
</style>