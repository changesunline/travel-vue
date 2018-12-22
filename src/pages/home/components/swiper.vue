<template>
	<div class="wrapper">
		<swiper :options="swiperOption" ref="mySwiper">
	    <!-- slides -->
	    <swiper-slide v-for="item of swiperList" :key="item.id">
	    	<img class="swiper-img" :src="item.imgURL">
	    </swiper-slide>
	    <!-- Optional controls -->
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
	</div>
</template>
<script type="text/javascript">
export default {
  name: 'HomeSwiper',
  data () {
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
          paginationClickable: true,
          loop: true,
          autoplay: 3000,
          autoplayDisableOnInteraction: false
        },
        swiperList: [
        	{
        		id: '1',
        		imgURL: 'http://img1.qunarzz.com/piao/fusion/1811/b7/1e9c4ca462741f02.jpg_750x200_842d5261.jpg'
        	},
        	{
        		id: '2',
        		imgURL: 'http://img1.qunarzz.com/piao/fusion/1811/a8/cb43c4ac6c215d02.jpg_750x200_83dee994.jpg'
        	},
        	{
        		id: '3',
        		imgURL: 'http://img1.qunarzz.com/piao/fusion/1812/47/a51fe403715df102.jpg_750x200_085792b6.jpg'
        	}
        ]
      }
    }
}
</script>
<style lang="stylus" scoped>
	// scoped表示只修饰当前组件中的类名，.swiper-pagination-bullet-active不在组件中显示
	.wrapper >>> .swiper-pagination
		.swiper-pagination-bullet-active
			background-color #fff
	.wrapper
		overflow hidden
		width 100%
		// height 26.67vw  viewport-width可以是视口宽度百分比，但设备不一定兼容
		height 0
		padding-bottom 26.67%
		background-color #ccc
		.swiper-pagination
			.swiper-pagination-bullet-active
				background-color #fff
		.swiper-img
			width 100%
</style>
