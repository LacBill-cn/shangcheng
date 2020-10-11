<template>
	<view class="goods_detail">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(item,index) in swipers" :key="index">	
			<image :src="item.pics_mid_url" mode=""></image>
				
			</swiper-item>
		</swiper>
		<view class="box1">
			<view class="price">
			<text>￥{{goods.goods_price}}</text>
				
			</view>
			<view class="goods_name">
				{{goods.goods_name}}
			</view>
			
		</view> 
		<view class="line">
		</view>
		<view class="box2">
			<view>货号：{{goods.goods_id}}</view>
			<view class="">
				库存：{{goods.goods_number}}
			</view>
		</view>
		<view class="line">
		</view>
		<view class="box3">
			<view class="tit">
				详情介绍
			</view>
			<view class="content">
				{{goods_introduce}}
			</view>
		</view>
		<view class="goods_nav">
			<uni-goods-nav :fill="true"  :options="options" :buttonGroup="buttonGroup"  @click="onClick" @buttonClick="buttonClick" />
			</view>
		</view>
		
</template>

<script>
	import uniGoodsNav from '@/components/uni-goods-nav/uni-goods-nav.vue'
	export default {
		data() {
			return {
				id:0,
				swipers:[],
				goods:[], options: [{
            icon: 'headphones',
            text: '客服'
        }, {
            icon: 'shop',
            text: '店铺',
            info: 2,
            infoBackgroundColor:'#007aff',
            infoColor:"red"
        }, {
            icon: 'cart',
            text: '购物车',
            info: 2
        }],
        buttonGroup: [{
          text: '加入购物车',
          backgroundColor: '#ff0000',
          color: '#fff'
        },
        {
          text: '立即购买',
          backgroundColor: '#ffa200',
          color: '#fff'
        }
        ]
			};
		},
		methods:{
			async	getGoodsList(){
				console.log(1)
					await uni.request({
						url:"https://api-hmugo-web.itheima.net/api/public/v1/goods/detail?goods_id="+this.id,
						success: res => {
							this.swipers=res.data.message.pics
							this.goods=res.data.message
							console.log(res)
							console.log(this.goods)
						}
					})
					
				},
				 onClick (e) {
				        uni.showToast({
				          title: `点击${e.content.text}`,
				          icon: 'none'
				        })
				      },
				      buttonClick (e) {
				        console.log(e)
				        this.options[2].info++
				      }
				    
		},
		components: {uniGoodsNav},
		onLoad(options) {
			console.log(options)
			this.id=options.id
			this.getGoodsList()
		}
	}
</script>

<style lang="scss">
	.goods_detail{
		swiper{
			height: 700rpx;
			image{
				width: 100%;
				height: 100%;
			}
		}
		.box1{
			padding: 10px;
			.price{
				font-size: 35rpx;
				color: $shop-color;
				line-height: 80rpx;
				
			}
			.goods_name{
				font-size: 32rpx;
				line-height: 60rpx;
			}
		}
		.box2{
			padding: 0 10px;
			font-size: 32rpx;
			line-height: 70rpx;
	}
	.box3{
		padding-bottom: 50px;
		.tit{
			font-size: 32rpx;
			padding-left: 10px;
			border-bottom:1px solid #eee ;
			line-height: 70rpx;
		}
		.content{
			padding: 10px;
			font-size: 28rpx;
			color: #333;
		}
	}
	}
	.line{
		height: 15rpx;
		width: 750rpx;
		background: #eee;
	}
	.goods_nav{
		position: fixed;
		bottom: 0;
		width: 100%;
	}
</style>
