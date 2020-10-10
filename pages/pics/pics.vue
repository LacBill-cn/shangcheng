<template>
	<view class="pics">
		<scroll-view scroll-y="true" class="left">
			
			<view 
			@click="leftClickHandle(index)"
			:class="active===index?'active':''" 
			v-for="(item,index) in cates" 
			 :key="index">
			 {{item.floor_title.name}}</view>
		</scroll-view>
		<scroll-view class="right" scroll-y="true">
			
			<view class="item"
			v-for="(item,index) in secondData"
		:key="index">
			    <text>{{item.name}}</text>
				<image :src="item.image_src" @click="previewImg(item.image_src)" ></image>
				
			</view>
			<text v-if="secondData.length ===0"> 暂无数据</text>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cates:[],
				active:0,
				secondData:[]
			}
			
		},
		methods: {
			async getPicsCate(){
				uni.request({
					url:"https://api-hmugo-web.itheima.net/api/public/v1/home/floordata",
					success: (res) => {
						this.cates=res.data.message
						console.log(this.cates)
						this.leftClickHandle(0)
					}
				})
			},
		
			
			leftClickHandle(index){
				console.log(index)
				this.active=index
				this.secondData= this.cates[index].product_list
				console.log(this.secondData)
			},
			previewImg (current) {
				const urls = this.secondData.map(item=>{
					return item.image_src
				})
				uni.previewImage({
					current,
					urls
				})
			}
			
			
		},
		onLoad() {
			this.getPicsCate()
		}
	}
</script>

<style lang="scss">
page{
	height: 100%;
}
.pics{
	height: 100%;
	display: flex;
	.left{
		width: 200rpx;
		height: 100%;
		border-right:1px solid #eee;
		view{
			height: 60px;
			line-height: 60px;
			color: #333;
			text-align: center;
			font-size: 30rpx;
			border-top:1px solid #eee;
		}
		.active{
			background: $shop-color;
			color: #fff;
		}
	}
	.right{
		height: 100%;
		width: 520rpx;
		margin: 10rpx auto;
		.item{
			image{
				width: 520rpx;
				height: 400rpx;
				border-radius: 5px;
			}
			text{
				font-size: 30rpx;
				line-height: 60rpx;
			}
		}
	}
}
</style>
