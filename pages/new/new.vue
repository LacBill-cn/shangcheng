<template>
	<view class="news">
		<news-item :list="news"></news-item>
	</view>
</template>

<script>
	import newsItem from '../../components/news-item/news-item.vue'
	export default {
		data() {
			return {
				news:[]
			}
		},
		methods: {
			getNews(){
				uni.request({
					url:"https://api-hmugo-web.itheima.net/api/public/v1/goods/search",
					success:res =>{
						
					this.news = res.data.message.goods
					
					console.log(res)
					}
				})
			}
		},
		comments:{"news-item":newsItem},
		onLoad() {
			this.getNews()
		}
	}
</script>

<style lang="scss">
.news{
		
	
}
</style>
