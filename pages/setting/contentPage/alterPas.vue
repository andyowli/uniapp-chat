<template>
	<view class="cont">
		<view class="header">
			<uni-icons type="left" @tap="back" style="margin-left: 20rpx;margin-right: 20rpx;font-size: 34rpx;"></uni-icons>
			<view class="name">修改密码</view>
			<button type="primary" @tap="Submit">完成</button>
		</view>
		
		<view class="input-cont">
			<view class="inputWrite">
				<input type="text" placeholder="输入账号" v-model="user"/>
				<input type="text" placeholder="输入密码" v-model="newPass"/>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				user:'',
				newPass:''
			}
		},
		methods:{
			back(){
				uni.navigateBack({
					url:'./setting/security',
					fail: (res) => {
						console.log(res)//打印错误信息
					}
				})
			},
			Submit(){
				if(this.user == ''){
					uni.showToast({
						title:'账号为空!',
						duration:2000,
						icon:'error'
					})
				}else if(this.newPass == ''){
					uni.showToast({
						title:'密码为空!',
						duration:2000,
						icon:'error'
					})
				}else if(this.user !== '' || this.newPass !== ''){
					uni.request({
						url:'http://localhost:3000/register/alterPass',
						data:{
							user:this.user,
							password:this.newPass
						},
						method:'Post',
						success: (res) => {
							console.log(res.data);
							uni.showToast({
								title:'密码修改成功!',
								duration:2000,
								icon:'success'
							})
							this.user = '';
							this.newPass = '';
						}
					})
				}
			}
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
		box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		margin-bottom: 30rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		button{
			margin-left: 0px;
			margin-right: 10px;
			font-size:24rpx;
		}
		.name{
			font-size: 30rpx;
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
</style>
