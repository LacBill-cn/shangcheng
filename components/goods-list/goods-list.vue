<template>
<view class="goods_list">
			<view class="goods_item" v-for = "item in goods" :key="item.goods_id">
				<image :src="item.goods_big_logo"></image>
			<view class="price">
				<text>￥{{item.goods_price}}</text>
				<text>库存：{{item.goods_number}}</text>
			</view>
			<view class="name">
				{{item.goods_name}}
			</view>
			</view>
			
		</view>
</template>

<script>
	export default {
		props:['goods'],
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.goods_list{
				padding:0 15rpx;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				.goods_item{
					background:#ffff;
					width: 355rpx;
					margin: 10rpx 0;
					padding: 15rpx;
					box-sizing: border-box;
					
					image{
						width: 80%;
						height: 300rpx;
						margin:  atuo;
						display: block;

					}
					.price{
						color:$shop-color ;
						font-size:36rpx;
						margin: 20rpx 0rpx 5rpx 0;
						text:nth-child(2){
							color: #F56C6C;
							letter-spacing: 5rpx;
							font-size: 28rpx;
							margin-left: 7rpx;
							font-weight: 700;
							margin-left: 35rpx;
						}
					}
				.name{
					font-size: 28rpx;
					line-height: 50rpx;
					padding-bottom: 15rpx;
					padding-top: 10rpx;
				}
				}
			}
			
</style>
