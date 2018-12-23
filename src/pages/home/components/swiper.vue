<template>
	<div class="wrapper">
		<swiper :options="swiperOption" v-if="showSwiper">
	    <!-- slides -->
	    <swiper-slide v-for="item of List" :key="item.id">
	    	<img class="swiper-img" :src="item.imgUrl">
	    </swiper-slide>
	    <!-- Optional controls -->
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
	</div>
</template>
<script type="text/javascript">
export default {
  name: 'HomeSwiper',
  props: {
  	List: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationClickable: true,
        loop: true,
        autoplay: 3000,
        autoplayDisableOnInteraction: false
      }
    }
  },
  computed: {
  	showSwiper () {
  		return this.List.length
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
