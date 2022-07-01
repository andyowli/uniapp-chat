<template>
	<view class="Index">
		<view class="search">
			<u-search placeholder="请输入搜索内容" v-model="keyword" :show-action="false"></u-search>
		</view>
		
		<view class="swiper">
			<u-swiper
					:list="list2"
					keyName="image"
					showTitle
					:autoplay="false"
					circular
					@click="jump"
			></u-swiper>
		</view>
	
		<!-- 瀑布流布局列表 -->
		<view class="pubuBox">
			<view class="pubuItem">
				<view class="item-masonry" v-for="(item, index) in filteredUser" :key="index">
					<image :src="item.img" mode=""></image>
					<view class="listtitle"> <!-- 这是没有高度的父盒子（下半部分） -->
						<view class="listtitle1">{{ item.name }}</view>
						<!-- <view class="listtitle2">
							<text class="listtitle2son">￥</text>
							{{ item.commdityPrice }}
						</view> -->
						<view class="listtitle3">
							<view class="user">
								<image src="../../static/images/96226079_p0_master1200.jpg" mode=""></image>
								<span>来自莫成尘的旗舰店</span>
							</view>
							<view ref="hearts" @tap="hearts(index)" style="color:#9da2a5">
								<span class="iconfont icon-dianzan"></span>
							</view>
						</view>
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
				keyword:'',
                albumWidth: 0,
				list2: [{
					id:1,
					image: '../../static/images/banner/shuiyue.png',
					title: '昨夜星辰昨夜风，画楼西畔桂堂东',
				},{
					id:2,
					image: '../../static/images/banner/yekong.png',
					title: '身无彩凤双飞翼，心有灵犀一点通'
				},{
					id:3,
					image: '../../static/images/banner/xinkong.png',
					title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
				}],
				comList: [{
					img: "../../static/images/girls/1.jpeg",
					name: '商品的名称，可以很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长',
					commdityPrice: 100
				}, {
					img: '../../static/images/girls/2.jpeg',
					name: '商品名称会在超出两行时候自动折叠',
					commdityPrice: 100
				},
				{
					img: '../../static/images/girls/3.jpeg',
					name: '只有一行标题时高度为39',
					commdityPrice: 100
				}, {
					img: '../../static/images/girls/4.jpeg',
					name: '具体样式您可以自定义',
					commdityPrice: 100
				}, {
					img: '../../static/images/girls/5.jpeg',
					name: 'vue的H5页面也是如此使用',
					commdityPrice: 100
				},{
					img: '../../static/images/girls/6.jpeg',
					name: 'vue的H5页面也是如此使用',
					commdityPrice: 100
				}], //商品列表
				
            }
        },
		computed:{
			//1.搜索功能，使用filter，return的是一个Boolean，运用match返回。
			//2.同时数据展示的v-for需要给filteredUser，而不是数据的数组。
			filteredUser(){
				return this.comList.filter((user) =>{
					return user.name.match(this.keyword);
				})
			}
		},
		methods:{
			jump(index){
				console.log(index);
				uni.navigateTo({
					url:`../../pages/sheqv/article?id=${index}`
				})
			},
			hearts(index){
				console.log(this.$refs.hearts[index].$el);
				let support = this.$refs.hearts[index].$el;
				if(support.style.color === 'rgb(157, 162, 165)'){
					support.style.color = 'red';
				} else if(support.style.color === 'red'){
					support.style.color = 'rgb(157, 162, 165)';
				}
				
				// new mojs.Burst({
				//     // 爆裂范围 {从多大 : 到多大}
				//     radius: {0: 50},
				//     // 动画挂载的父元素, 如果不填默认挂载到 <body>
				//     parent: heart,
				//     // 动画延迟的贝塞尔曲线函数
				//     easing:  mojs.easing.bezier(0.1, 1, 0.3, 1),
				//     // 动画延迟时间
				//     duration: 1500,
				//     // 在动画动之前等待的时间 (这里一般设置150ms方便减少低端机型可能会存在的卡顿)
				//     delay: 300,
				//     // 扩散的粒子配置
				//     children: {
				//         duration: 750,
				//         // 粒子大小变换 {从多大 : 到多大}
				//         // rand(from, to) rand函数可以帮我们随机出一个区间的值
				//         radius: {0: 'rand(0, 25)'},
				//         // 形状选择, 这里我们选择了 “圆形”
				//         shape: 'circle',
				// 		shape: 'rect',
				// 		// shape: 'zigzag',
				//         // 粒子可选的填充色
				//         fill: ['#1abc9c', '#2ecc71', '#00cec9', '#3498db', '#9b59b6', '#fdcb6e', '#f1c40f', '#e67e22', '#e74c3c', '#e84393']
				//     },
				//     // 透明度
				//     opacity: 0.6,
				//     // 生成的粒子数量
				//     count: 10,
				//     onStart(){
				//         // 动画触发前的钩子函数     
				//     },
				//     onComplete(){
				//         // 动画完成后的钩子函数     
				//     }
				// }).play();
			}
		}
    }
</script>

<style lang="scss" scoped>
	@import '../..//static/css/icon/iconfont.css';
  //瀑布流
	.Index {
	    width: 100%;
	    height: 100%;
		padding-top: var(--status-bar-height);
		
		.search,.swiper{
			padding: 20px;
		}
		.swiper{
			margin-top: -14px;
		}
	}
	
	.pubuBox {
		padding: 22rpx;
	}

	.pubuItem {
		column-count: 2;
		column-gap: 20rpx;
	}

	.item-masonry {
		box-sizing: border-box;
		border-radius: 15rpx;
		overflow: hidden;
		background-color: #fff;
		break-inside: avoid;
		/*避免在元素内部插入分页符*/
		box-sizing: border-box;
		margin-bottom: 20rpx;
		box-shadow: 0px 0px 28rpx 1rpx rgba(78, 101, 153, 0.14);
		
		image{
			width: 100%;
		}
	}

	.item-masonry image {
		width: 100%;
		height: 170px;
	}

	.listtitle {
		font-size: 24rpx;
		padding: 20rpx;

		.listtitle1 {
			line-height: 39rpx;
			text-overflow: -o-ellipsis-lastline;
			overflow: hidden;
			text-overflow: ellipsis;
			display: -webkit-box;
			-webkit-line-clamp: 2;
			line-clamp: 2;
			-webkit-box-orient: vertical;
			min-height: 39rpx;
			max-height: 78rpx;
		}

		// .listtitle2 {
		// 	color: #ff0000;
		// 	font-size: 32rpx;
		// 	line-height: 32rpx;
		// 	font-weight: bold;
		// 	padding-top: 22rpx;

		// 	.listtitle2son {
		// 		font-size: 32rpx;
		// 	}
		// }

		.listtitle3 {
			display: flex;
			justify-content: space-between;
			align-items: center;
			font-size: 28rpx;
			color: #909399;
			line-height: 32rpx;
			padding-top: 22rpx;
			
			.user{
				overflow: hidden;
				text-overflow: ellipsis;
				// word-break: break-all;
				width: 220rpx;
				white-space: nowrap;
				
				image{
					width: 30px;
					height: 30px;
					border-radius: 50%;
					vertical-align: middle;
				}
				span{
					margin-left: 6px;
				}
			}
		}
		.heart{
			.red{
				color: red;
			}
			.bla{
				color: black;
			}
		}
	}
	
</style>