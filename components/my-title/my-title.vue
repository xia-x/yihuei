<template>
	<view>
		<view class="title">
			<view>{{titlename}}</view>
			<view class="haed_more">
				<view>MORE</view>
				<uni-icons type="arrowright" size="13" color="#a6a6a6"></uni-icons>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		// name: "title",
		// props: {
		// 	titlename:{
		// 		type:String,
		// 		value:''
		// 	}
		// },
		props:["titlename"],
		data() {
			return {
			 	
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>	
	  .title{
	  	    font-size: 36rpx;
	  		display: flex;
	  		justify-content: space-between;
	  		.haed_more{
	  			color: $font-color-c;
	  			font-size: 26rpx;
	  			line-height: 60rpx;
	  			display: flex;		
	  		}  
	  	}
	  
</style>
