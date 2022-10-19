<template>
	<view class="app">
		<uni-swiper-dot :info="info" :current="current" field="content" :mode="mode" :style="{height:swiperheight+'px'}">
			<swiper class="swiper-box" @change="change" :style="{height:swiperheight+'px'}">
				<swiper-item v-for="(item ,index) in info" :key="index">
					<view class="swiper-item">
						<img :src= item.img alt="">
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<view class="store">
			<view class="name">
				<h3>选择分店</h3>
			</view>
			<view class="stores">
				<view class="dian" v-for="(item,index) in stores" :key="index" @tap="goDetail(index)">
					<view class="di">
						<img :src=item.img alt="">
						<view class="information">
							<h3>{{item.name}}</h3>
							<h4>电话:{{item.phone}}</h4>
							<h4>地址:{{item.address}}</h4>
						</view>
					</view>
					<view class="border"></view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiperheight:0,
				current: 0,
				mode: 'default',
				info:[
					{
						img:"../../static/image/IMG_20221017_224318.jpg"
					},
					{
						img:"../../static/image/IMG_20221017_224336.jpg"
					},
					{
						img:"../../static/image/IMG_20221017_224350.jpg"
					}
				],
				stores:[
					{
						img:'../../static/image/stores/万达店.png',
						name:'时点造型(万达店)',
						phone: '0535-6906215',
						address:'烟台市芝罘区万达金街B1-208'
					},{
						img:'../../static/image/stores/开发区店.png',
						name:'时点造型(开发区店)',
						phone: '15335451688',
						address:'烟台市开发区万行爱琴海购物公园1号门二楼'
					},{
						img:'../../static/image/stores/万象城店.png',
						name:'时点造型(万象城店)',
						phone: '0535-6906215',
						address:'烟台市莱山区万象城步行街东首A1-6'
					},{
						img:'../../static/image/stores/弘阳广场店.png',
						name:'时点造型(弘阳广场店)',
						phone: '0535-6266522',
						address:'烟台市芝罘区大海阳路弘阳广场2F'
					},{
						img:'../../static/image/stores/龙口店.png',
						name:'时点造型(龙口店)',
						phone:'13053547303',
						address:'烟台市龙口市东城区东莱街道南巷商贸街时点造型'
					}
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(750)
					this.swiperheight = height; // 让data中定义的swiperheight高度等于计算过后的高度
					console.log(this.swiperheight)
				}
			});
		
		},
		methods: {
			change(e) {
				this.current = e.detail.current;
			},
			//页面跳转
			goDetail(index){
				var stores = JSON.stringify(this.stores[index])
				uni.navigateTo({
					url:'./details?a='+stores
				})
			}
		}
	}
</script>

<style lang="scss">
	.app{
		padding: 10rpx;
		.swiper-item{
			width: 100%;
			height: 100%;
			img{
				width: 100%;
				height: 100%;
			}
		}
		.store{
			margin-top: 30rpx;
			.stores{
				.dian{
					width: 100%;
					margin-top: 10px;
					.di{
						display: flex;
						.information{
							margin-left: 30rpx;
							h3{
								font-weight: bold;
								color: #333333;
							}
							h4{
								margin-top: 3%;
							}
						}
						img{
							width: 30%;
							height: 100%;
						}
					}
					.border{
						margin-top: 2px;
						border-bottom: 1px solid #E5E5E5;
					}
				}
			}
		}
	}
	
</style>
