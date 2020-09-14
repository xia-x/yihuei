<template>
	<view>
		<view class="navs_con">
			<view class="navs" v-for="item in navs" :key="item.id">
				<image :src="item.url"></image>
				<view class="item_title">
					<view>{{item.subhaed}}</view>
					<view>{{item.haed}}</view>
				</view>
			</view>
		</view>
		<view class="art_con">
			<title :titlename="Arttile"></title>
			<view class="art_list">
				<view class="list_itme" v-for="item in artgoods" :key="item.id">
					<image :src="item.url"></image>
					<view>{{item.name}}</view>
					<view>￥{{item.price}}</view>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	import title from "@/components/title/title.vue"
	export default {
		data() {
			return {
			   navs:[
				   {url:'../../static/img/market_nav01.png',subhaed:'Coutom Made',haed:'个性定制'},
				   {url:'../../static/img/market_nav02.png',subhaed:'Art derivatives',haed:'艺术衍生'},
				   {url:'../../static/img/market_nav03.png',subhaed:'Original art',haed:'原创艺术'},
				   {url:'../../static/img/market_nav04.png',subhaed:'Cridits exchange',haed:'造艺作品'}
			   ],
			   Arttile:"艺术衍生",
			   artgoods:[
				    {url:'../../static/img/market_goods01.png',name:'风荷书签',price:'118'},
					{url:'../../static/img/market_goods02.png',name:'风荷书签',price:'218'},
					{url:'../../static/img/market_goods01.png',name:'风荷书签',price:'339'},
			   ]
			}
		},
		methods: {
			
		},
		components:{
			title,
		}
	}
</script>

<style lang="scss" scoped>
	.navs_con{
		margin: 16rpx 33rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		font-size: 26rpx;
		.navs{
		     margin-bottom: 16rpx;
			 position:relative;
			.item_title{
				position: absolute;
				top: 70rpx;
				left: 70rpx;
				view:nth-child(1){
					font-size: 16rpx;
					margin-bottom: 8rpx;
					color: $font-color-c;
				}
			}
			image{
				width: 332rpx;
				height: 200rpx;	
				
			}
			
		}
	}
    .art_con{
		background: #fff;
		padding: 25rpx 33rpx;
		.art_list{
			display: flex;
			flex-wrap: wrap;
			justify-content:space-between;
			text-align: center;
			.list_itme{
				margin: 22rpx 0rpx;
				view:nth-child(2){
					margin: 24rpx auto 20rpx;
					font-size: 26rpx;
				}
				view:nth-child(3){
					font-size: 22rpx;
					color: $price_color;
				}
				image{
					width: 332rpx;
					height: 475rpx;
				}
			}
			
			
		}
	}
</style>
