<template>
	<view class="top_nav_con">
		<view class="topnav_item" v-for="(item,index) in topnav" :key="index" @click="tabnav(index)">
			<view :class="[navindex==index?'item_after':'']">{{item.name}}</view>
		</view>
		<image src="../../static/img/find_btn_edit.png"></image>
	</view>
</template>

<script>
	export default {
		props: {
			topnav:{
				type:Array,
				value:''
			},
			navindex:{
				type:Number,
				value:0
			},
		},
		data() {
			return {
				navindex:0,
			}
		},
		methods: {
			tabnav(index){
				console.log(index)
				this.$emit("changeindex",index)
			},
		}
	}
</script>

<style lang="scss" scoped>
	.top_nav_con{
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
</style>
