<template>
	<view>
		<view v-if="pageLoad">
		<view class="d-title">{{pageData.data.title}}</view>
		 
		<view class="d-content">
		<rich-text type="text" :nodes="pageData.data.content"></rich-text>
		</view>
		</view>
	</view>
</template>

<script>
	var app= require("../../common/common.js"); 
	var id;
	export default{
		data:{
			pageLoad:false, 
			pageData:{}
		},
		onLoad:function(option){
			id=option.id;
			this.getPage();
		},
		 
		methods:{
			getPage:function(){
				var that=this;
				uni.request({
					url:app.apiHost+"?m=article&ajax=1&a=show&id="+id,
					success:function(data){
						that.pageLoad=true;
						that.pageData=data.data.data;
						 
					}
				})
			} 
		},
	}
</script>

<style>
</style>