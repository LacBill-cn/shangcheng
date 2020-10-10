<template>
	<view class="contact">
		<image class="img" src="http://www.itcast.cn/2018czydz/images/gywmban.jpg"></image>
		<view class="info">
			<view @click="phone">
				联系电话: 17373672779 ( 点击拨打 )
			</view>
			<view class="">
				联系地址:陕西省西安市西咸新区庞东村
			</view>
		</view>
		<map class="map" :scale="scale" :longitude="longitude" :latitude="latitude" :markers="markers"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude: 108.663337,
				latitude: 34.399967,
				scale:15,
				markers:[
					{
						longitude: 108.663337,
						latitude: 34.399967,
						iconPath:"https://image.baidu.com/search/detail?ct=503316480&z=0&ipn=d&word=滑稽&hs=2&pn=0&spn=0&di=98890&pi=0&rn=1&tn=baiduimagedetail&is=0%2C0&ie=utf-8&oe=utf-8&cl=2&lm=-1&cs=3581134888%2C2217954696&os=2594737345%2C1019862292&simid=55861289%2C1050261542&adpicid=0&lpn=0&ln=30&fr=ala&fm=&sme=&cg=&bdtype=0&oriquery=滑稽&objurl=http%3A%2F%2Fwww.17qq.com%2Fimg_biaoqing%2F28841531.jpeg&fromurl=ippr_z2C%24qAzdH3FAzdH3Fooo_z%26e3B80qq_z%26e3Bv54AzdH3Fktw5qtg2AzdH3F89lmnm8_z%26e3Bip4s&gsm=1&islist=&querylist=",
						width:30,
						height:30,
					}
				]
			}
		},
		methods: {
			phone(){
				console.log("123")
				uni.makePhoneCall({
					phoneNumber:'17373672779',
					
				})
			}
		}
	}
</script>

<style lang="scss">
.contact{
	.img{
		width: 750rpx;
		height: 320rpx;
	}
	.info{
		padding: 10rpx 20rpx;
		font-size: 30rpx;
		view{
			line-height: 80rpx;
			border-bottom:1px solid #eee ;
		}
	}
	.map{
		width: 750rpx;
		height: 700rpx;
	}
}
</style>
