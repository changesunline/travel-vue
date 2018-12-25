<template>
	<div class="icons">
    <swiper class="swiper-container" :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>
<script type="text/javascript">
export default {
  name: 'HomeIcons',
  props: {
    List: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.List.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    },
    showSwiper () {
      return this.List.length
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icons >>> .swiper-container
    width 100%
    height 0
    padding-bottom 54%
  .icons >>> .swiper-pagination
    position absolute
    bottom 0
    .swiper-pagination-bullet
      width .12rem
      height .12rem
  .icons
    overflow hidden
    width 100%
    height 0
    padding-bottom 54%
    .icon
      position relative
      overflow hidden
      float left
      width 25%
      height 0
      box-sizing border-box
      padding-bottom 25%
      .icon-img
        position absolute
        top 0
        left 0
        right 0
        bottom .50rem
        padding-top .3rem
        .icon-img-content
          display block
          margin 0 auto
          height 100%
      .icon-desc
        position absolute
        right 0
        left 0
        bottom 0
        height .50rem
        line-height .50rem
        text-align center
        color $darkTextColor
        ellipsis()
</style>
