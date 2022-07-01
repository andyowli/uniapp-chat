<template>
	<view class="">
		<view v-for="(item,index) in list" :key="item.id">
			{{item.cont}}
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				id:null, //定义id变量，用于接收参数
				list:[
					{id:1,cont:'这是1'},
					{id:2,cont:'这是2'},
					{id:3,cont:'这是3'},
				]
			}
		},
		onLoad(options) { //options用于获取上级页面参数
			this.id = options.id;
			console.log(options)
		}
	}
</script>

<style>
</style>