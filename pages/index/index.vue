<template>
	<view class="content">
		<view class="top-bar">
			<view class="top-bar-left">
				<image src="../../static/icon/liaotian.png"></image>
				<span>Talkie</span>
			</view>
			<view class="top-bar-right">
				<view class="add">
					<image src="../../static/icon/more.png" @click="add"></image>
				</view>
			</view>
		</view>
		
		<view class="input-contain">
			<view class="input-name">
				<input type="text" placeholder="请输入好友名称" v-model="searchFriends">
			</view>
		</view>
		
		
		<view class="main">
			<view class="friends" @tap="addUser">
				<view class="friends-list">
					<view class="friends-list-l">
						<text class="tip">1</text>
						<image src="../../static/images/tianjiahaoyou.png"></image>
					</view>
					<view class="friends-list-r">
						<view class="top">
							<view class="name">好友请求</view>
							<view class="time"></view>
						</view>
						<view class="contents">用户添加您位好友，请查看</view>
					</view>
				</view>
			</view>
			
			<view class="friends"  @tap="user" v-for="(item,index) in filteredUser" :key="index">
				<view class="friends-list">
					<view class="friends-list-l">
						<text class="tip">1</text>
						<image :src="item.img"></image>
					</view>
					<view class="friends-list-r">
						<view class="top">
							<view class="name">{{item.username}}</view>
							<view class="time">{{item.date}}</view>
						</view>
						<view class="contents">出来玩！</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchFriends:'',
				list:[
					{
						date:'13:21',
						username:'秋天的柠檬',
						img:'../../static/images/girls/6.jpeg'
					},
					{
						date:'13:21',
						username:'夏天的桑蚕',
						img:'../../static/images/girls/5.jpeg'
					},
					{
						date:'13:21',
						username:'冬天的飞雪',
						img:'../../static/images/girls/9.jpeg'
					}
				]
			}
		},
		onLoad: function(options) {
				setTimeout(function () {
					console.log('start pulldown');
			}, 1000);
		},
		onPullDownRefresh() {
			console.log('refresh');
			setTimeout(function () {
				uni.stopPullDownRefresh();
			}, 1000);
		},
		methods: {
			selectClick(index){
				console.log(index)
			},
			user(){
				console.log(11111)
				uni.navigateTo({
					url:'../chat/chat'
				})
			},
			add(){
				uni.navigateTo({
					url:'../group/createGroup'
				})
			},
			addUser(){
				uni.navigateTo({
					url:'../addUser/addUser'
				})
			}
		},
		computed:{
			//1.搜索功能，使用filter，return的是一个Boolean，运用match返回。
			//2.同时数据展示的v-for需要给filteredUser，而不是数据的数组。
			filteredUser(){
				return this.list.filter((user) =>{
					return user.username.match(this.searchFriends);
				})
			}
		},
	}
</script>

<style lang="scss" scoped>
	.content {
		padding-top: var(--status-bar-height);
	}
	.top-bar{
		width: 100%;
		height: 88rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		.top-bar-left{
			padding-left: 20px;
		}
		.top-bar-right{
			padding-right: 20px;
		}
		.top-bar-left{
			image{
				width: 58rpx;
				height: 58rpx;
				border-radius: 16rpx;
			}
			span{
				font-size: 44rpx;
			}
			image,span{
				vertical-align: middle;
			}
		}
		.top-bar-right{
			image{
				width: 52rpx;
				height: 52rpx;
			}
		}
	}
	
	.input-contain{
		height: 30px;
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 30px 0 30px 0;
		.input-name{
			width: 90%;
			height: 40px;
			background: #f3f5f7;;
			border-radius: 20px;
			input{
				padding: 10px 0 0 20px;
			}
		}
	}
	
	.main{
		.friends{
			border-bottom: 1px dashed rgba(0,0,0,0.2);
			.friends-list{
				height: 96rpx;
				padding: 20rpx;
				.friends-list-l{
					float: left;
					position: relative;
					image{
						width: 96rpx;
						height: 96rpx;
						border-radius: 24rpx;
						background-color:  #FFE431;
					}
					.tip{
						position: absolute;
						z-index: 10;
						top: -6rpx;
						left: 68rpx;
						height: 36rpx;
						min-width: 36rpx;
						background: $uni-color-warning;
						border-radius: $uni-border-radius-circle;
						font-size: $uni-font-size-sm;
						color: $uni-text-color-inverse;
						line-height: 36rpx;
						text-align: center;
					}
				}
				.friends-list-r{
					padding-left: 128rpx;
					.top{
						height: 50rpx;
						.name{
							float: left;
							font-size: 36rpx;
							color: #272832;
							font-weight: 400;
							line-height: 50rpx;
						}
						.time{
							float: right;
							font-size: $uni-font-size-sm;
							color: $uni-text-color-disable;
						}
					}
				}
				.contents{
					font-size: $uni-font-size-base;
					color: $uni-text-color-grey;
					line-height: 40rpx;
					white-space: nowrap;
					text-overflow: ellipsis;
					overflow: hidden;
					word-break: break-all;
				}
			}
		}
	}
</style>

