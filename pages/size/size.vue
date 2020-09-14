<template>
	<view>
		<input @input="onKeyInput" />
		<button @click="getsize">换算</button>
		<view>{{size}}</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				size:0,
				inputValue:0,
			}
		},
		methods: {
			onKeyInput: function(event) {
			    this.inputValue = event.target.value
				console.log(this.inputValue)
			 },
			getsize(){
				console.log(this.inputValue)
				this.size = this.inputValue/1.44
			}
		}
	}
</script>

<style>

</style>
