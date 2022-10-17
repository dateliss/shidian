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
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					// uni-app 提供了 upx2px 方法，将对应的 rpx 值转换成了 px
					let height = res.windowHeight - uni.upx2px(750)
					this.swiperheight = height; // 让data中定义的swiperheight高度等于计算过后的高度
					console.log(this.swiperheight)
				}
			});
		
		},
		methods: {
			change(e) {
						this.current = e.detail.current;
			}
		}
	}
</script>

<style lang="scss">
	.app{
		.swiper-item{
			width: 100%;
			height: 100%;
			img{
				width: 100%;
				height: 100%;
			}
		}
	}
	
</style>
