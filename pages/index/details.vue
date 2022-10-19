<template>
	<view class="app" >
		<uni-swiper-dot :info="info" :current="current" field="content" :mode="mode" :style="{height:swiperheight+'px'}">
			<swiper class="swiper-box" @change="change" :style="{height:swiperheight+'px'}">
				<swiper-item v-for="(item,index) in info" :key="index">
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
						img:'../../static/image/stores/万达店.png'
					}
				],
			};
		},
		onLoad(option) {
			//var data = JSON.parse(option.a)
			//this.stores = data
			//传过来一个对象，不需要for循环遍历，直接使用数组名字输出即可
			//console.log(data)
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(750)
					this.swiperheight = height; // 让data中定义的swiperheight高度等于计算过后的高度
					console.log(this.swiperheight)
				}
			});
		
		},
		methods:{
			change(e) {
				this.current = e.detail.current;
			},
		}
	}
</script>

<style lang="scss">

</style>
