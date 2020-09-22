<template>
	<view>
		<view class="topnav_con">
			<view class="topnav_item" v-for="(item,index) in topnav" :key="index" @click="tabnav(index)">
				<view :class="[navindex==index?'item_after':'']">{{item.name}}</view>
			</view>
			<image src="../../static/img/find_btn_edit.png"></image>
		</view>
		<view class="example-body">
			<swiper class="swiper" :indicator-dots="true">
				<swiper-item>
					<uni-grid :showBorder="false" :column="3" :highlight="false" @change="change">
						<uni-grid-item v-for="(item, index) in subnav" :index="index" :key="index">
							<view class="grid-item-box">
								<image :src="item.url" class="image" mode="aspectFill" />
								<text class="text">{{ item.name }}</text>
							</view>
						</uni-grid-item>
					</uni-grid>
				</swiper-item>
			</swiper>
		</view>
		<view class="artinfo_con" v-for="(item,index) in list" :key="index">
			 <view class="artinfo_userinfo">
				 <view class="user_name">
					 <image :src="item.userimg"></image>
					 <view>{{item.username}}</view>
				 </view>
				 <button class="user_btn" >关注</button>
			 </view>
			 <view class="item_content">
				 <view>{{item.title}}</view>
				 <view>
					 <text>画展日期:{{item.artshowtime}}</text>
					 <text>开幕仪式:{{item.starttime}}</text>
				 </view>
				 <view @click="openmoer">
					 <text>展开</text>
					 <uni-icons v-show="!moerflag" type="arrowdown" size="13" color="#a6a6a6"></uni-icons>
					 <uni-icons v-show="moerflag" type="arrowup" size="13" color="#a6a6a6"></uni-icons>
					 <view v-show="moerflag" >{{item.content}}</view>
			     </view>
			 </view>
			 <view class="itme_imgs">
				 <image v-for="(item,index) in item.urls" :key="index" :src="item"></image>
			 </view>
			 <view class="item_collect">
				<view>
					<image src="../../static/img/find_icon_love.png"></image>
					<view>{{item.collect}}</view>
				</view>
				<view>
					<image src="../../static/img/find_icon_information.png"></image>
					<view>{{item.comment}}</view>
				</view>
			</view>
			<view class="item_comments">
				<view v-for="(item,index) in item.comments" :key="index">
					<text class="comments_name">{{item.name}}: </text>
					<text>{{item.text}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniSwiperDot from "@/components/uni-swiper-dot/uni-swiper-dot.vue"
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	export default {
		data() {
			return {
				topnav:[
					{name:"推荐",id:'1'},{name:"最新",id:'2'},{name:"关注",id:'3'},
				],
				navindex:0,
				subnav:[
					{url:'../../static/img/find_banner01.png',name:"插画",id:'01'},
					{url:'../../static/img/find_banner02.png',name:"插画",id:'02'},
					{url:'../../static/img/find_banner03.png',name:"插画",id:'03'},
					{url:'../../static/img/find_banner04.png',name:"插画",id:'04'},
					{url:'../../static/img/find_banner05.png',name:"插画",id:'05'},
					{url:'../../static/img/find_banner06.png',name:"插画",id:'06'},
				],
				showBorder:false,
				moerflag:false,
			    list:[
					{
					  userimg:"../../static/img/my_userimg.png",
					  username:"曼艺术画展",
					  title:"如迷个展张炯",
					  artshowtime:'2020/9/18-10/17',
					  starttime:'2018/9/8 14:00-16:00',
					  content:"此次画展主题是......",
					  urls:["../../static/img/find_banner01.png",
					        "../../static/img/find_banner02.png",
					        "../../static/img/find_banner03.png",
					        "../../static/img/find_banner04.png",
					        "../../static/img/find_banner05.png",
					        "../../static/img/find_banner06.png",
							"../../static/img/find_banner02.png",
							"../../static/img/find_banner03.png",
							"../../static/img/find_banner04.png",
							],
					  collect:295,
					  comment:30,
					  comments:[
						  {name:"老王",text:'好看了'},
						  {name:"夏夏",text:'好看了'},
						  {name:"夏夏",text:'随便一张都是背景'},
					  ]
					},
					{
					  userimg:"../../static/img/my_userimg.png",
					  username:"曼艺术画展",
					  title:"如迷个展张炯",
					  artshowtime:'2020/9/18-10/17',
					  starttime:'2018/9/8 14:00-16:00',
					  content:"此次画展主题是......",
					  urls:["../../static/img/find_banner01.png",
					        "../../static/img/find_banner02.png",
					        "../../static/img/find_banner03.png",
					        "../../static/img/find_banner04.png",
					        "../../static/img/find_banner05.png",
					        "../../static/img/find_banner06.png",
							"../../static/img/find_banner02.png",
							"../../static/img/find_banner03.png",
							"../../static/img/find_banner04.png",
							],
					  collect:295,
					  comment:30,
					  comments:[
						  {name:"老王",text:'好看了'},
						  {name:"夏夏",text:'好看了'},
						  {name:"夏夏",text:'随便一张都是背景'},
					  ]
					}
				]
			}
		},
		methods: {
			tabnav(index){
				console.log(index)
				this.navindex=index
			},
			change(e) {
				console.log(e)
				let {index} = e.detail
				this.list[index].badge && this.list[index].badge++
				uni.showToast({
					title: `点击第${index+1}个宫格`,
					icon: 'none'
				})
			},
			openmoer(){
				this.moerflag =!this.moerflag 
			}
		},
		components:{
			uniGrid,
			uniGridItem,
			uniSwiperDot,
		}
	}
</script>

<style lang="scss" scoped>
	.topnav_con{
		padding: 30rpx 32rpx 0rpx 133rpx;
		text-align: center;
		display: flex;
		justify-content:space-between;
		background: #fff;
		.topnav_item view{
			width: 116rpx;
			font-size: 34rpx;
			font-weight: 800rpx;
			color: $font-color-a;
		}
		.item_after{
			padding-bottom: 30rpx;
			border-bottom: 4rpx solid;
		}
		image{
			width: 50rpx;
			height: 48rpx;
			margin-right: 32rpx;
		}
	}
	.example-body{
		padding: 16rpx;
		margin-top: 5rpx;
		background: #fff;
		.swiper{
			height: 550rpx;
		}
		.grid-item-box{
			margin: 15rpx;
			background: #fff;
		    box-shadow: 0 0 10rpx rgba(0, 0, 0, 0.1);
			border-radius: 10rpx;
			width: 200rpx;
			height: 250rpx;
			text-align: center;
			font-size: 26rpx;
			image{
				width: 200rpx;
				height: 150rpx;
				border-radius: 10rpx 10rpx 0rpx 0rpx;
			}
			.text{
				margin: 16rpx auto;
			}
			
		}
	}
	.artinfo_con{
		font-size: 26rpx;
		margin-top: 16rpx;
		background: #fff;
		padding: 34rpx;
		.artinfo_userinfo{
			display: flex;
			.user_name{
				display: flex;
				line-height: 100rpx;
				image{
					width: 100rpx;
					height: 100rpx;
				}
			}
			.user_btn{
				width: 112rpx;
				height: 50rpx;
				background: transparent;
				font-size: 28rpx;
				line-height: 50rpx;
				padding: 0rpx;
			    margin-top: 30rpx;
				margin-right: 0rpx;
			}
			
		}
	    .item_content{
			view:nth-child(1){
				padding: 18rpx;
			}
			view:nth-child(2){
				display: flex;
				flex-direction: column;
				padding: 18rpx;
			}
			view:nth-child(3){
				color:$font-color-b;
				padding: 18rpx;
			}
		}
		.itme_imgs{
			margin: 26rpx auto;
			image{
				width: 215rpx;
				height: 215rpx;
				margin: 6rpx;
				border-radius: 0rpx;
			}
		}
	    .item_collect{
		    display: flex;
			image{
				width: 50rpx;
				height: 50rpx;
			}
			view:nth-child(1),
			view:nth-child(2){
				display: flex;
				width: 200rpx;
				view{line-height: 50rpx;}
			}
	    }
	    .item_comments{
			margin-top: 50rpx;
		    .comments_name{
			  color: $font-color-b;
		    }
	     }
	}

</style>
