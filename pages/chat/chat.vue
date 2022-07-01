<template>
	<view class="chat-box">
		<view class="header">
			<uni-icons type="left" @tap="back" style="font-size: 34rpx;display: flex;align-items: center;height: 100%;margin-left: 38rpx;"></uni-icons>
			<view class="name">知道</view>
			<view class="more">...</view>
		</view>
		

		<view class="chat-main" @tap="closeAll" ref="chatMain">
			<view class="chat-ls" id="chat-list">
				<view class="chat-time">9:00</view>
				<!-- 左 -->
				<view class="chat-tou-left" v-for="(item,a) in message" :key="a">
					<image :src="item.imgUrl" mode="" class="chat-img" ></image>
					<view class="chat-mesg-l">
						
						<view class="" v-if="item.types ==0">
							<p>{{item.message}}</p>
						</view>
						
						<view class="" v-if="item.types ==1" @tap="bigImg(item.message)">
							<image :src="item.message" mode="widthFix"></image>
						</view>
					</view>
				</view>
				
				<!-- 录音 -->
				<view class="chat-tou-right" v-for="(p,k) in sound" :key="k" @tap="playVoice(p.message)">
					<view class="chat-mesg-l" style="display: flex;">
						<image :src="p.soundImg" class="soundImg"></image>
						<span>{{p.time}}</span>
					</view>
					<image :src="p.imgUrl" class="chat-img"></image>
				</view>
				<!-- 地图 -->
				<view class="chat-tou-right" v-for="(z,x) in maps" style="padding: 4px;" @tap="openLocation(z)">
					<view class="chat-mesg-l">
						<span>{{z.name}}</span>
						<span style="font-size: 24rpx;">{{z.address}}</span>
						<map class="photomap" :latitude="z.latitude1" :longitude="z.longitude2" :markers="covers(z)"></map>
					</view>
					<image :src="z.imgUrl" class="chat-img"></image>
				</view>
			</view>
		</view>
		
		<!-- 视频 -->
		<chatVideo v-if="hide"></chatVideo>
		
		<!-- 底部栏 -->
		<view class="chat-input">
			<view class="chat-botton">
				<view class="left-icon">
					<image src="../../static/images/yuyin.png" @click="voice()"></image>
				</view>
				<view class="input-box">
					<input type="text" value="" v-model="inputValue" v-show="inputText"/>
					<view class="speak" v-show="btnSpeak" @touchstart="touchstart" @touchend="touchend">
						<span>按住说话</span>
					</view>
				</view>
				<view class="right-icon">
					<image src="../../static/images/biaoqin.png" @tap="showEmjio"></image>
					<image src="../../static/images/tianjia.png" @tap="showMore"></image>
				</view>
			</view>
			
			<!-- 表情 -->
			<view class="moreEmjio" v-show="emjio">
				<emjio @emotion="emotion"></emjio>
			</view>
			
			<view class="more1" v-show="xuan">
				<ul class="box-inner">
					<li v-for="(a,b) in photo" @click="Fn(a.method)">
						<image :src="a.photoImg"></image>
						<span>{{a.title}}</span>
					</li>
				</ul>
			</view>
		</view>
		
		
	</view>
</template>

<script>
	import chatVideo from '../chat/chatVideo/video.vue';
	import emjio from './emjio.vue';
	const recorderManager = uni.getRecorderManager();
	const innerAudioContext = uni.createInnerAudioContext();
	innerAudioContext.autoplay = true;
	export default{
		data(){
			return {
				hide:false, //视频通话变量
				selectedUser:[],
				timer:'', //录音时的时间函数
				nowTime:'',//录音时长
				name:'',
				address:'',
				latitude1:'',
				longitude2:'',
				latitude:'',
				longitude:'',
				voicePath: '', //音频录制的文件路径
				mags:[],
				inputValue:'',
				inputText:true,
				btnSpeak:false,
				xuan:false,//显示input更多
				emjio:false,
				imgUrls:[], //放大图片
				sound:[], //音频信息数组
				maps:[], //地图信息数组
				img:'',
				message:[
					{
						id:'a',
						types:0,
						imgUrl:'../../static/images/96226079_p0_master1200.jpg',
						message:'我给你发送了一条消息消息消息消息消息消息消息消息消息消息消息消息消息消息消息消息'
					},
					{
						id:'a',
						types:1,
						imgUrl:'../../static/images/96226079_p0_master1200.jpg',
						message:'../../static/images/girls/8.jpeg'
					},
					{
						id:'a',
						types:1,
						imgUrl:'../../static/images/96226079_p0_master1200.jpg',
						message:'../../static/images/girls/2.jpeg'
					}
				],
				photo:[
					{photoImg:'../../static/zhaopian.png',title:'图片',method:'meadia'},
					{photoImg:'../../static/shipin.png',title:'视频',method:'open'},
					{photoImg:'../../static/wenjianjia.png',title:'文件'},
					{photoImg:'../../static/a-luxianfangxiangdaohangweizhi.png',title:'位置',method:'map'}
				]
			}
		},
		components:{
			emjio,
			chatVideo
		},
		onLoad(){
			this.enterSend();
		},
		methods:{
			back(){
				uni.navigateBack({
					url:'../index/index'
				})
			},
			//接受表情
			emotion(e){
				console.log(e);
			},
			getMsg(){
				let msg = this.message;
				console.log(msg);
				for(let i=0;i<msg.length;i++){
					 
				}
			},
			//放大图片
			bigImg(e){
				console.log('aa');
				//把数据数组中的图片路径放进imgUrls
				for(let i = 0;i < this.message.length;i++){
					if(this.message[i].types == 1){
						this.imgUrls.push(this.message[i].message);
					}
					console.log(this.imgUrls);
				}
				
				//获取图片索引
				let index = 0;
				for(let i = 0;i < this.imgUrls.length;i++){
					if(this.imgUrls[i] ==e){
						index = i;
					}
				}
				// 预览图片
				uni.previewImage({
					current:index, //获取当前显示图片的链接/索引值
					urls: this.imgUrls,
					longPressActions: {
						itemList: ['发送给朋友', '保存图片', '收藏'],
						success: function(data) {
							console.log('选中了第' + (data.tapIndex + 1) + '个按钮,第' + (data.index + 1) + '张图片');
						},
						fail: function(err) {
							console.log(err);
						}
					}
				});
			},

			enterSend(){
				//消息输入框发送创建列表
				document.onkeydown = (event) =>{
					var content = document.getElementById('chat-list');
					var e = event || window.event;
					if(e && e.keyCode == 13){
						if(this.inputValue !== ''){
							// console.log(111);
							var myMessage = document.createElement('view');
							var chater ='<view class="chat-mesg-r">'+
										this.inputValue+
										'</view>'+
										'<image src="../../static/images/96226079_p0_master1200.jpg" class="chat-img"></image>'
							myMessage.className = 'chat-tou-right';
							myMessage.innerHTML = chater;
							this.inputValue = '';
							// console.log(myMessage);
							content.appendChild(myMessage);
						}else if(this.inputValue == ''){
							uni.showToast({
								title:'消息为空!',
								duration:2000,
								icon:'error'
							})
						}
					}
				}
			},
			voice(){
				//语音按钮切换
				if(this.inputText == true){
					this.inputText = false;
					this.btnSpeak = true;
				}else{
					this.inputText = true;
					this.btnSpeak = false;
				}
			},
			//开始录音
			touchstart(){
				console.log('开始');
				let i = 0;
				this.timer = setInterval(() => {
					i++;
					this.nowTime = i;
					console.log(this.nowTime);
					if(i>10){
						clearInterval(this.timer)
					}
				},1000);
				recorderManager.start({
					format: "mp3"
				});
			},
			//结束录音
			touchend(){
				console.log('结束');
				clearInterval(this.timer);
				recorderManager.stop();
				
				recorderManager.onStop((res) => {
					console.log('recorder stop' + JSON.stringify(res));
					this.voicePath = res.tempFilePath;
					let yuYinMessage = {
						
						imgUrl:'../../static/images/96226079_p0_master1200.jpg',
						soundImg:'../../static/images/shengboyuyinxiaoxi.png',
						time:this.nowTime,
						message:res.tempFilePath
					}
					// console.log(yuYinMessage);
					this.sound.push(yuYinMessage);
					console.log(this.sound);
				});
			},
			//音频播放
			playVoice(e) {
				console.log('播放录音');
				innerAudioContext.autoplay = true;
				innerAudioContext.src = e;
				innerAudioContext.play();
			},
			//map地图位置图标
			map(){
				uni.chooseLocation({
					success: res => {
						console.log(res);
						let data = {
							name:res.name,
							address:res.address,
							latitude1:res.latitude, //纬度
							longitude2:res.longitude, //经度
							imgUrl:'../../static/images/96226079_p0_master1200.jpg',
						}
						this.maps.push(data);
						console.log(this.maps);
					}
				});
			},
			//位置定位
			covers(e){
				console.log(e);
				let map = [{
					latitude: e.latitude1,
					longitude: e.longitude2,
					iconPath: '../../static/dingweiweizhimudedi.png'
				}]
				return (map);
			},
			//点击查看地图位置
			openLocation(e){
				console.log(e);
				uni.openLocation({
					latitude: Number(e.latitude),
					longitude: Number(e.longitude),
					name:e.name,
					address:e.address,
					success: function () {
						console.log('success');
					},
					fail:function(){
						console.log('err');
					}
				})
			},
			showMore(){
				if(!this.xuan){
					this.xuan = true;
				}else{
					this.xuan = false;
				}
				
				if(this.emjio == true){
					this.emjio = false;
				}
			},
			showEmjio(){
				if(!this.emjio){
					this.emjio = true;
					
				}else{
					this.emjio = false;
				}
				
				if(this.xuan == true){
					this.xuan = false;
				}
			},
			//图标循环绑定事件
			Fn (method) {
				this[method]()
			},
			//图片图标
			meadia(){
				uni.chooseImage({
					count: 6, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: function (res) {
						// console.log(JSON.stringify(res.tempFilePaths));
						console.log(res.tempFilePaths[0].path);
						var photo = res.tempFilePaths[0];
						console.log(photo);
						
						let that = this;
						that.img = photo;
						console.log(that.img);
					}
				});
			},
			//视频图标
			open(){
				if(this.hide === false){
					this.hide = true;
				}else{
					this.hide = false;
				}
			},
			closeAll(){
				if(this.emjio == true){
					this.emjio = false;
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.chat-box{
		padding-top: var(--status-bar-height);
		height: 100%;
	}
	.header{  
		width: 100%;
		height: 88rpx;
		// background: $uni-bg-color;
		box-shadow: 0px 1px 0px 0px rgba(0,0,0,0.1);
		display: flex;
		justify-content: space-between;
		// z-index: 2;
		.back,.more{
			font-size: 40rpx;
		}
		.back{
			margin: 20rpx;
		}
		.more{
			margin: 10rpx 24rpx 0 0;
		}
		.name{
			margin: 24rpx;
		}
	}
	
	.chat-main{
		height: 74%;
		padding: 10px;
		overflow: hidden;
		overflow-y: auto;
	}
	.chat-ls{
		.chat-time{
			font-size: $uni-font-size-sm;
			color: rgba(39,40,50,0.3);
			line-height: 34rpx;
			padding: 20rpx 0;
			text-align: center;
		}
		
		.chat-tou-left,::v-deep .chat-tou-right{
			display: flex;
			padding: 20rpx 0;

			.chat-mesg-l,.chat-mesg-r{
				width: 300rpx;
				background: #f3f5f7;
				border-radius: 20rpx;
				padding: 20rpx;
				margin-left: 30rpx;
				overflow: hidden;
				
				p{
					height: 100%;
					display:flex;
					align-items:center;
					font-size: 28rpx;
				}
				image{
					max-width: 100%;
					max-height: 140px;
					border-radius: 10px;
				}
				span{
					width: 300rpx;
					white-space:nowrap;
					overflow:hidden;
					text-overflow:ellipsis;
					display: block;
					margin:10px 0 10px 0;
				}
				.photomap{
					width: 300rpx;
					height: 190rpx;
				}
				.soundImg{
					width: 68px;
					height: 40px;
				}
			}
		}
		/deep/.chat-tou-right,.chat-tou-left{
			.chat-img{
				width: 80rpx;
				height: 80rpx;
				border-radius: 20rpx;
				margin-left: 20rpx;
			}
		}
	}
	
	/deep/.chat-tou-right{
		float: right;
	}
	
	.chat-input{
		width: 100%;
		position: fixed;
		bottom: 0;
		z-index: 10;
		.chat-botton{
			height:80px;
			display: flex;
			align-items: center;
			background:rgba(244,244,244,1);
			box-shadow:0px 1px 0px 0px rgba(0,0,0,0.1);
			.left-icon{
				padding-left:12rpx ;
				padding-right:12rpx ;
				display: flex;
				align-items: center;
				image{
					width: 56rpx;
					height: 56rpx;
				}
			}
			.input-box{
				width: 68%;
				input,.speak{
					width: 100%;
					height:72rpx;
					background:rgba(255,255,255,1);
					border-radius:10rpx;
				}
				input{
					padding-left: 20rpx;
				}
				.speak{
					position: relative;
					font-size: 32rpx;
					span{
						position: absolute;
						top: 50%;
						left: 50%;
						transform: translate(-50%, -50%);
					}
				}
				
			}
			.right-icon{
				width: 188rpx;
				display: flex;
				align-items: center;
				justify-content: space-evenly;
				margin-left: 10px;
				image{
					width: 56rpx;
					height: 56rpx;
				}
			}
		}
		
		.moreEmjio{
			width: 100%;
			height: 200px;
			overflow: hidden;
			overflow-y: auto;
			background: #FBFBFD;
		}
		
		.more1{
			position: relative;
			width: 100%;
			height: 200px;
			background: #FFFFFF;
			.box-inner {
			  position: absolute;
			  top: 0;
			  left: 0;
			  width: 100%;
			  height: 100%;
			  display: flex;
			  justify-content: space-around;
			  flex-wrap: wrap;
			}
			li{
			  list-style: none;
			  text-align: center;
			  color: #ffffff;
			  width: 12%;
			  height: 26%;
			  text-align: center;
			  margin-top: 20rpx;
			  
				image{
				  width: 84rpx;
				  height: 84rpx;
				}
				span{
				  color: #007AFF;
				  font-size: 26rpx;
				}
			}
		}
	}
</style>
