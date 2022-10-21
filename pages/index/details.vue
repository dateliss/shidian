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
		<view class="classification">
			<view>
			    <uni-segmented-control :current="fen" :values="items" @clickItem="onClickItem" styleType="text" activeColor="#E9BC7B"></uni-segmented-control>
			    <view class="content">
			        <view v-show="fen === 0">
						<view class="bulk"></view>
			            <uni-segmented-control :current="genre" :values="genres" @clickItem="genress" styleType="text" activeColor="#E9BC7B"></uni-segmented-control>
			            <view class="content1">
			                <view v-show="genre === 0">
			                    <view class="details" v-for="(item,index) in details" :key="index">
			                    	<view class="img">
										<img :src= item.img alt="">
			                    	</view>
									<view class="detail">
										<h4>{{item.name}}</h4>
										<p class="designer">{{item.designer}}</p>
										<p class="price">￥{{item.price}}</p>
									</view>
									<view class="buy">
										
									</view>
			                    </view>
								<uni-collapse>
									<uni-collapse-item title="折叠内容">
										<view class="details" v-for="(item,index) in details" :key="index">
											<view class="img">
												<img :src= item.img alt="">
											</view>
											<view class="detail">
												<h4>{{item.name}}</h4>
												<p class="designer">{{item.designer}}</p>
												<p class="price">￥{{item.price}}</p>
											</view>
											<view class="buy">
												
											</view>
										</view>
									</uni-collapse-item>
								</uni-collapse>
			                </view>
			                <view v-show="genre === 1">
			                    选项卡2的内容
			                </view>
			                <view v-show="genre === 2">
			                    选项卡3的内容
			                </view>
			            	<view v-show="genre === 3">
			            	    选项卡3的内容
			            	</view>
							<view v-show="genre === 4">
							    选项卡3的内容
							</view>
							<view v-show="genre === 5">
							    选项卡3的内容
							</view>
			            </view>
			        </view>
			        <view v-show="fen === 1">
			            选项卡2的内容
			        </view>
			        <view v-show="fen === 2">
			            选项卡3的内容
			        </view>
					<view v-show="fen === 3">
					    选项卡3的内容
					</view>
			    </view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				stores:{},
				swiperheight:0,
				current: 0,
				mode: 'default',
				info:[
					{
						img:'../../static/image/wanda/wanda7.jpg'
					},{
						img:'../../static/image/wanda/wanda2.jpg'
					},{
						img:'../../static/image/wanda/wanda3.jpg'
					},{
						img:'../../static/image/wanda/wanda4.jpg'
					},{
						img:'../../static/image/wanda/wanda5.jpg'
					},{
						img:'../../static/image/wanda/wanda6.jpg'
					},
				],
				items:['优惠','发型师','精选作品','评价'],
				fen:0,
				genres:['热门','洗吹','护理','烫染','接发'],
				genre:0,
				details:[
					{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'精剪+造型『首席设计师』',
						price:69,
						designer:'首席设计师',
						count:255
					},{
						img:'../../static/image/wanda/wanda11.jpg',
						name:'烫/染/直【不满意重做】',
						price:339,
						designer:'资深设计师 | 含护理',
						count:133
					},{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'烫/染【不满意重做】',
						price:199,
						designer:'资深设计师',
						count:195
					},{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'精剪+造型『技术总监』',
						price:128,
						designer:'技术总监',
						count:93
					},{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'精剪+造型『技术首席』',
						price:99,
						designer:'首席设计师',
						count:45
					},{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'贴片无痕接发[ 50厘米优质发 ]',
						price:798,
						designer:'资深设计师',
						count:15
					},{
						img:'../../static/image/wanda/wanda10.jpg',
						name:'烫/染/直【不满意重做】',
						price:499,
						designer:'技术总监',
						count:3
					},
				]
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
			onClickItem(e){
				if(this.fen !== e.currentIndex){
					this.fen = e.currentIndex
				}
			},
			genress(e){
				if(this.genre !== e.currentIndex){
					this.genre = e.currentIndex
				}
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
	.classification{
		.content{
			.bulk{
				height: 20rpx;
			}
			.content1{
				.details{
					margin-top: 20px;
					display: flex;
					.img{
						height: 80px;
						margin-right: 20rpx;
						img{
							height: 100%;
						}
					}
					.detail{
						.designer{
							font-size: 15rpx;
							color: #6B6B6B;
							margin-top: 10px;
						}
						.price{
							margin-top: 10px;
							color: #FF5A01;
							font-weight: bold;
							font-size: 40rpx;
						}
					}
				}
			}
		}
	}
}
</style>
