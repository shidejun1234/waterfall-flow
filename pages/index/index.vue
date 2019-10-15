<template>
	<view class="content">
		<view hidden>
			<block v-for="(a,b) in imgList">
				<block v-for="(item,index) in a">
					<image @load="imageLoad" :data-src="item.src" :src="item.src" mode="widthFix"></image>
				</block>
			</block>
		</view>
		<view>
			<block v-for="(item,index) in imgList1">
				<image :src="item.src" mode="widthFix" :style="`left: ${item.left}upx;top: ${item.top}upx;`"></image>
			</block>
		</view>
	</view>
</template>

<script>
	var colCount //定义列数
	var colHeightArry = [] //定义列高度数组
	var imgWidth = 375 //单张图片的宽度

	colCount = parseInt(750 / imgWidth) //计算出列数

	for (var i = 0; i < colCount; i++) {
		colHeightArry[i] = 0
	}

	export default {
		data() {
			return {
				title: 'Hello',
				imgList: [
					[{
						src: "../../static/1.jpg"
					}, {
						src: "../../static/2.jpg"
					}, {
						src: "../../static/david-travis-554904-unsplash.jpg"
					}, {
						src: "../../static/3.jpg"
					}, {
						src: "../../static/4.jpg"
					}, {
						src: "../../static/5.jpg"
					}, {
						src: "../../static/6.jpg"
					}, {
						src: "../../static/7.jpg"
					}, {
						src: "../../static/8.jpg"
					}, {
						src: "../../static/9.jpg"
					}, {
						src: "../../static/10.jpg"
					}, {
						src: "../../static/11.jpg"
					}, {
						src: "../../static/12.jpg"
					}, {
						src: "../../static/13.jpg"
					}, {
						src: "../../static/14.jpg"
					}, {
						src: "../../static/15.jpg"
					}, {
						src: "../../static/16.jpg"
					}, {
						src: "../../static/17.jpg"
					}, {
						src: "../../static/1569568584_xcx2.jpg"
					}, {
						src: "../../static/18.jpg"
					}, {
						src: "../../static/19.jpg"
					}, {
						src: "../../static/20.jpg"
					}]
				],
				imgList1: []
			}
		},
		onLoad() {

		},
		onReachBottom() {
			var imgList = [{
				src: "../../static/1.jpg"
			}, {
				src: "../../static/2.jpg"
			}, {
				src: "../../static/david-travis-554904-unsplash.jpg"
			}, {
				src: "../../static/3.jpg"
			}, {
				src: "../../static/4.jpg"
			}, {
				src: "../../static/5.jpg"
			}, {
				src: "../../static/6.jpg"
			}, {
				src: "../../static/7.jpg"
			}, {
				src: "../../static/8.jpg"
			}, {
				src: "../../static/9.jpg"
			}, {
				src: "../../static/10.jpg"
			}, {
				src: "../../static/11.jpg"
			}, {
				src: "../../static/12.jpg"
			}, {
				src: "../../static/13.jpg"
			}, {
				src: "../../static/14.jpg"
			}, {
				src: "../../static/15.jpg"
			}, {
				src: "../../static/16.jpg"
			}, {
				src: "../../static/17.jpg"
			}, {
				src: "../../static/1569568584_xcx2.jpg"
			}, {
				src: "../../static/18.jpg"
			}, {
				src: "../../static/19.jpg"
			}, {
				src: "../../static/20.jpg"
			}]
			this.imgList.push(imgList)
		},
		methods: {
			imageLoad(e) {
				var src = e.currentTarget.dataset.src
				var width = e.detail.width
				var height = e.detail.height
				height = imgWidth * height / width
				var minValue = colHeightArry[0] //定义最小的高度
				var minIndex = 0 //定义最小高度的下标
				for (var i = 0; i < colCount; i++) {
					if (colHeightArry[i] < minValue) { //如果最小高度组数中的值小于最小值
						minValue = colHeightArry[i] //那么认为最小高度数组中的值是真正的最小值
						minIndex = i //最小下标为当前下标
					}
				}
				this.imgList1.push({
					src: src,
					left: minIndex * imgWidth,
					top: minValue
				})
				colHeightArry[minIndex] += height
			}
		}
	}
</script>

<style>
	image {
		position: absolute;
		width: 355upx;
		margin: 10upx;
		/* 布局transition效果 */
		transition: all .4s;
	}
</style>
