<template>
	<view class="desContain">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;"></uni-icons>
			<view class="name">注销</view> 
		</view>
		
		<view class="input-cont">
			<h3>验证身份</h3>
			<view class="inputWrite">
				<input type="text" placeholder="请输入账号" v-model="user"/>
				<input type="text" placeholder="请输入密码" v-model="paw"/>
			</view>
		</view>
		<button type="primary" style="width: 70%;border-radius: 40rpx;" @tap="next">下一步</button>
		
		<view class="overlay" v-if="mask"></view>
		<view class="dialog" v-if="dia">
			<view class="dialog__header">注销账号</view>
			<view class="dialog__message">
				真的要注销您当前的账号吗？
			</view>
			<view class="dialog__footer">
				<button class="dialog_btn button--default" @tap="close">取消</button>
				<button class="dialog_btn button--default dialog__confirm" @tap="Submit">确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				user:'',
				paw:'',
				mask:false,
				dia:false
			}
		},
		methods:{
			back(){
				uni.navigateTo({
					url:'../security'
				})
			},
			next(){
				if(this.user == ''){
					uni.showToast({
						title:'账号为空!',
						duration:2000,
						icon:'error'
					})
				}else if(this.paw == ''){
					uni.showToast({
						title:'密码为空!',
						duration:2000,
						icon:'error'
					})
				}else if(this.user !== '' || this.paw !== ''){
					this.mask = !this.mask;
					this.dia = !this.dia;
				}
			},
			close(){
				this.mask = !this.mask;
				this.dia = !this.dia;
			},
			Submit(){
				uni.request({
					url:'http://localhost:3000/register/del',
					data:{
						user:this.user,
						password:this.paw
					},
					method:'Post',
					success: (res) => {
						console.log(res.data);
						uni.showToast({
							title:'密码注销成功!',
							duration:2000,
							icon:'success'
						})
						uni.navigateTo({
							url:'../../login/login'
						})
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.desContain{
		padding-top: var(--status-bar-height);
		position: relative;
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
		.input-cont{
			// padding: 20rpx;
			// position: absolute;
			// top: 50%;
			margin-top: 110px;
			h3{
				text-align: center;
			}
			.inputWrite{
				padding: 60rpx;
				// border-radius: 10rpx;
				// box-shadow:0px 1px 10px 0px rgba(0,0,0,0.1);
				input{
					padding: 20rpx;
					border-bottom: 1px dashed rgba(0,0,0,0.2);
				}
			}
		}
		.overlay{
			position: fixed;
			top: 0;
			left: 0;
			z-index: 1;
			width: 100%;
			height: 100%;
			background-color: rgba(0, 0, 0, 0.7);
		}
		.dialog{
			position: fixed;
			top: 45%;
			left: 50%;
			z-index: 1;
			width: 320px;
			overflow: hidden;
			font-size: 16px;
			background-color: #fff;
			border-radius: 16px;
			-webkit-transform: translate3d(-50%, -50%, 0);
			transform: translate3d(-50%, -50%, 0);
			-webkit-backface-visibility: hidden;
			backface-visibility: hidden;
			-webkit-transition: 0.3s;
			transition: 0.3s;
			-webkit-transition-property: opacity, -webkit-transform;
			transition-property: opacity, -webkit-transform;
			transition-property: transform, opacity;
			transition-property: transform, opacity, -webkit-transform;
			
			.dialog__header{
				padding-top: 26px;
				font-weight: 500;
				line-height: 24px;
				text-align: center;
			}
			.dialog__message{
				padding: 26px 24px;
				overflow-y: auto;
				font-size: 14px;
				line-height: 20px;
				white-space: pre-wrap;
				text-align: center;
				word-wrap: break-word;
			}
			.dialog__footer{
				display: flex;
				overflow: hidden;
				
				.dialog_btn{
					position: relative;
					display: inline-block;
					box-sizing: border-box;
					height: 44px;
					margin: 0;
					padding: 0;
					font-size: 16px;
					text-align: center;
					border-radius: 2px;
					cursor: pointer;
					-webkit-transition: opacity 0.2s;
					transition: opacity 0.2s;
					-webkit-appearance: none;
					flex: 1;
				}
			}
		}
		.button--default{
			background: #fff;
		}
		.dialog__confirm{
			color: #ee0a24;
		}
	}
</style>
