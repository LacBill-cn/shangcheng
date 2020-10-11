<template>
	<view class="goods_list">
	 <goods-list @goodsItemClick="goDetail" :goods = "goods"></goods-list>
	 <view class="isOver" v-if="flag">
	 	------我是有限的------
	 </view>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue'
	export default {
		data() {
			return {
				goods:[],
				flag:false
			}
		},
		components:{"goods-list":goodsList},
		methods: {
			// 获取商品列表数据
			async	getGoodsList(){
						console.log("获取商品数据")
					await uni.request({
						url:"https://api-hmugo-web.itheima.net/api/public/v1/goods/search",
						success: res => {
							console.log(res)
							this.goods=res.data.message.goods
							console.log(goods)
						}
					})
					
				},
				goDetail(id){
					uni.navigateTo({
						url: '../goods-detail/goods-detail?id='+id,
						
					});
				}
		},
		onLoad() {
			this.getGoodsList()
		},
		onReachBottom() {
			
		}
	}
</script>

<style lang="scss">

.goods_list{
	background: #eee;
}

</style>
