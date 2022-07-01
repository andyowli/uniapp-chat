<template>
	<u-index-list :index-list="indexList">
		<template v-for="(item, index) in itemArr">
			<!-- #ifdef APP-NVUE -->
			<!-- <u-index-anchor ></u-index-anchor> -->
			<!-- #endif -->
			<u-index-item>
				<!-- #ifndef APP-NVUE -->
				<u-index-anchor :text="indexList[index]"></u-index-anchor>
				<!-- #endif -->
				<view class="list-cell" >
					<image :src="item.img" class="img"></image>
					<span>{{item.userName}}</span>
				</view>
			</u-index-item>
		</template>
	</u-index-list>
</template>

<script>
	export default {
		data() {
			return {
				indexList: ["A","B","C","D","E","F","G","H","I","J"],
				itemArr: [
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					{img:'../../static/images/96226079_p0_master1200.jpg',userName:'冬天的太阳'},
					// ['列表A1','列表A2','列表A3'],
					// ['列表B1','列表B2','列表B3'],
					// ['列表C1','列表C2','列表C3'],
					// ['列表D1','列表B2','列表B3'],
					// ['列表E1','列表B2','列表B3'],
					// ['列表F1','列表B2','列表B3'],
					// ['列表G1','列表B2','列表B3'],
				]
			}
		}
	}
</script>

<style lang="scss" scoped>
	.list-cell {
		// display: flex;
		box-sizing: border-box;
		width: 100%;
		padding: 10px 24rpx;
		overflow: hidden;
		color: #323233;
		font-size: 14px;
		line-height: 24px;
		background-color: #fff;
		
		image{
			width: 40px;
			height: 40px;
			margin-left: 10px;
			border-radius: 10px;
			vertical-align: middle;
		}
		span{
			margin-left: 10px;
		}
	}
</style>