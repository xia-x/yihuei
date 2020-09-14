<template>
	<view class="home_con">
		<uni-swiper-dot :info="banners" :current="current" field="content" :mode="mode">
			<swiper class="swiper"  @change="change" :autoplay="autoplay" :interval="interval" :duration="duration">
				<swiper-item   v-for="(item ,index) in banners" :key="index">
				   <image :src="item.url"></image>
				   <image class="searchicon" src="../../static/img/homepage_icon_search.png"></image>
				</swiper-item>
			</swiper>
	    </uni-swiper-dot>
		<view class="navs_con">
		  <view class="navs_list" v-for="(item,index) in navs" :key="index">
			  <view class="item_title">{{item.title}}</view>
			  <view class="item_subhaed">{{item.subhaed}}</view>
		  </view>
		</view>
		<view class="works_con">
			<title :titlename="workstitle"></title>
			<view class="wosks_list">
				<view v-for="item in works" :key="item.id">
					<image :src="item.url"></image>
					<text>{{item.name}}</text>
				</view>
			</view>
		</view>
	    <view class="exhibit_con">
			<title :titlename="exhibititle"></title>
			<view class="exhibit_list">
				<view class="exhibit_list_item" v-for="item in exhibits" :key="item.id">
					<image :src="item.url"></image>
					<view class="itme_name">{{item.name}}</view>
					<view class="itme_time">{{item.time}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniSwiperDot from "@/components/uni-swiper-dot/uni-swiper-dot.vue"
	import uniIcons from "@/components/uni-icons/uni-icons.vue"
	import title from "@/components/title/title.vue"
	export default {
		data() {
			return {
			 exhibititle:"近期展览",
			 workstitle:"作品推荐",
			 autoplay:true,
			 interval:2000,
			 duration:500,
             banners:[
				 {id:'01',url:"../../static/img/home_banner.png"},
				 {id:'02',url:"../../static/img/home_banner.png"},
				 {id:'03',url:"../../static/img/home_banner.png"}
			 ],
			 navs:[
				 {title:"艺术家",subhaed:"ARTIST"},
				 {title:"作品",subhaed:"WORKS"} ,
				 {title:"阅读",subhaed:"READ"} ,
				 {title:"定制",subhaed:"COUSTOMZED"} 
			 ],
			 works:[
				 {id:'01',url:'../../static/img/home_works01.png',name:"风景"},
				 {id:'02',url:'../../static/img/home_works02.png',name:"风景"},
				 {id:'03',url:'../../static/img/home_works03.png',name:"风景"} 
			 ],
			 exhibits:[
				 {id:'01',url:'../../static/img/home_exhibits01.png',name:"李宗津油画作品展:澄湖",time:"北京艺术中心|2016/09/20/10/29"},
				 {id:'02',url:'../../static/img/home_works02.png',name:"李宗津油画作品展:澄湖",time:"北京艺术中心|2016/09/20/10/29"}
			 ],
			 current: 0,
			 mode: 'default',
			}
		},
		methods: {
            change(e) {
               this.current = e.detail.current;
            }
		},
        components:{
			"uni-swiper-dot":uniSwiperDot,
			"uni-icons":uniIcons,
			 title,
		}
	}
</script>

<style lang="scss" scoped>
	.swiper{
		position: relative;
		height: 416rpx;
		image{
			width: 100%;
			height: 100%;
		}
		.searchicon{
			width: 50rpx;
			height: 50rpx;
			position: absolute;
			right: 32rpx;
			top: 32rpx;
			z-index: 100rpx;
		}
	}
    .navs_con{
		display: flex;
		justify-content: space-between;
		font-size: 32rpx;
		background: #fff;
		.navs_list{
			text-align: center;
			margin: 37rpx auto 26rpx;
			.item_subhaed{
				font-size: 12rpx;
				margin-top: 12rpx;
				color: $font-color-c;
			}
		}
		
	}
	.works_con{	
		background: #fff;
		margin-top: 16rpx;
	    padding: 16rpx 36rpx;
		.wosks_list{
			display: flex;
			justify-content: space-between;
			margin-top: 16rpx;
			view{
				margin-right:16rpx;
				text-align: center;
			}
			image{
				width: 216rpx;
				height: 310rpx;
			}
			text{
				
				font-size: 22rpx;
			}
		}	
	}
    .exhibit_con{
		background: #fff;
		margin-top: 16rpx;
		padding: 16rpx 36rpx;
		.exhibit_list{
			font-size: 36rpx;
		    .exhibit_list_item{
				image{
					width: 100%;
					height: 506rpx;
					margin-top: 16rpx;
				}
				.itme_time{
					font-size: 24rpx;
					color: $font-color-c;
			    }
			}
		}
		
	}
</style>
