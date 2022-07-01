<template>
	<view class="createGroup">
		<view class="header">
			<uni-icons type="left" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;" @tap="back"></uni-icons>
			<view class="name">设置</view>
		</view>
		<view class="group-img">
			<image src="../../static/images/96226079_p0_master1200.jpg" class="img"></image>
		</view>
		<!-- 搜索 -->
		<view class="input-contain">
			<view class="input-name">
				<input type="text" placeholder="请输入群名称">
			</view>
		</view>
		<!-- 用户列表 -->
		<view class="userBox">
			<view v-for="(item,index) in list" :key="index" class="user-list">
				<checkbox @tap="getUserName()"/>
				<image :src="item.img" class="img"></image>
				<view class="userName">{{item.userName}}</view>
			</view>
		</view>
		<view class="button">创建</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				// getUser:'',
				dis:false,
				list:[
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'222'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'333'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
				
				]
			}
		},
		methods:{
			getUserName(){
				if(this.dis = !this.dis){
					console.log('选中');
				}else{
					console.log('取消');
				}
			},
			back(){
				uni.navigateBack({
					url:'../../index/index'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.createGroup{
		height: 100%;
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
		.group-img{
			height: 140px;
			display: flex;
			justify-content: center;
			align-items: center;
			image{
				width: 60px;
				height: 60px;
			}
		}
		.input-contain{
			height: 30px;
			display: flex;
			justify-content: center;
			align-items: center;
			.input-name{
				width: 90%;
				height: 40px;
				background: #fff;
				border-radius: 20px;
				input{
					padding: 10px 0 0 20px;
				}
			}
		}
		.userBox{
			height: 67%;
			padding: 20rpx;
			overflow: hidden;
			overflow-y: scroll;
			.user-list{
				padding: 20px;
				display: flex;
				justify-content: flex-start;
				align-items: center;
				image{
					width: 40px;
					height: 40px;
					margin-left: 10px;
					border-radius: 10px;
				}
				.userName{
					margin-left: 20px;
				}
			}
		}
		.button{
			width: 100%;
			height: 50px;
			background: yellow;
			border-radius: 10px;
			position: fixed;
			bottom: 0;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
</style>