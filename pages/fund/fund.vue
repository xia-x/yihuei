<template>
	<view>
		<button @click="opensize">打开</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			opensize(){
				uni.navigateTo({
					url:'../size/size'
				})
			}
		}
	}
</script>

<style>

</style>
