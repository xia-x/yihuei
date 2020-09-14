<template>
	<view>
		<view class="myinfo_top">
			<image class="setup" src="../../static/img/my_btn_setup.png"></image>
			<view class="userinfo">
				<image src="../../static/img/my_userimg.png"></image>
				<view>{{username}}</view>
				<view>{{userlabel}}</view>
			</view>
			<view class="menu_con">
				<view class="menu_list" v-for="(item,index) in menuarr" :key="index">
					<image :src="item.url"></image>
					<view>{{item.menuname}}</view>
				</view>
			</view>
		</view>
		<view class="miannav_con">
			<view class="miannav_list" v-for="(item,index) in miannav" :key="index">
				<view>{{item}}</view>
				<uni-icons type="arrowright" size="20" color="#a6a6a6"></uni-icons>
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcons from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				username:"WELOCME",
				userlabel:"不重复别人,不重复自己，到死也要创造",
				menuarr:[
					{url:"../../static/img/my_icon_historicalrecords.png",menuname:"历史记录"},
					{url:"../../static/img/my_icon_consignment.png",menuname:"代发货"},
					{url:"../../static/img/my_icon_artwork.png",menuname:"我的艺术品"},
					{url:"../../static/img/my_icon_coupons.png",menuname:"优惠卷"},
					{url:"../../static/img/my_icon_wishlist.png",menuname:"心愿清单"}
				],
				miannav:["我的订单","收货地址","意见反馈","关于我们","联系客服"]
			}
		},
		methods: {
			
		},
		components:{
			"uni-icons":uniIcons,
		}
	}
</script>

<style lang="scss"  scoped>
	.myinfo_top{
		background:$font-color-a;
		position: relative;
		.setup{
			width: 50rpx;
			height: 50rpx;
			position: absolute;
			top: 18rpx;
			right: 32rpx;
		}
		.userinfo{
		    padding-top: 87rpx;
			text-align: center;
			color: #fff;
			font-size: 34rpx;
			image{
				width: 160rpx;
				height: 160rpx;
				margin-bottom: 8rpx;
			}
			view:nth-child(3){
				font-size: 22rpx;
			}
		}
		.menu_con{
			margin-top: 80rpx;
			display: flex;
			justify-content: space-between;
			.menu_list{
				text-align:center;
				color: #fff;
				margin: 37rpx auto;
				image{
					width: 66rpx;
					height: 66rpx;
				}
				view{
					font-size: 26rpx;
				}
			}
		}
	}
	.miannav_con{
		margin-top: 20rpx;
		background: #FFFFFF;
		.miannav_list{
			font-size: 34rpx;
			display: flex;
			justify-content: space-between;
			padding: 42rpx;
		}
	}  
</style>
