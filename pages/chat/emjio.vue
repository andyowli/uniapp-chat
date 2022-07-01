<template>
	<view class="emjio">
		<view class="emjio-line" v-for="(line,i) in emjio" :key="i">
			<view class="emjio-line-item" v-for="(item,index) in line" :key="index" @tap="clickEmjio(item)">{{item}}</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				emjio:[
					['😀','😁','😂','🤣','😃','😄','🙄','😏'],
					['😅','😆','😉','😊','😋','😎','😣','😥'],
					['😍','😘','😗','😙','😚','☺️','😮','🤐'],
					['🙂','🤗','🤔','😐','😑','😶','😯','😪'],
					['😫','😴','😌','😛','😜','🤤','😒','😓'],
					['😔','😕','🙃','🤑','😲','😟','🙁','😖'],
					['😤','😢','😭','😦','😨','😩','😬','😱'],
					['😳','😵','😡','😠','😷','🤒','🤢','🤧'],
					['😇','🤠','🤡','🤥','🤓','😈','👻','💩'],
					['😺','😸','😹','😻','😼','😽','🙀','😿']
				]
			}
		},
		methods:{
			clickEmjio(e){
				this.$emit('emotion',e)
			}
		}
	}
</script>

<style lang="scss">
	.emjio{
		width: 100%;
		height: 460rpx;
		padding: 10rpx;
		box-sizing: border-box;
		.emjio-line{
			display: flex;
			.emjio-line-item{
				flex:1;
				text-align: center;
			}
		}
	}
</style>
