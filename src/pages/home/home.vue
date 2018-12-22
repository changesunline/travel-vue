<template>
	<div>
		<home-header></home-header>
  	<home-swiper></home-swiper>
  	<home-icons></home-icons>
  	<home-recommend></home-recommend>
	</div>
</template>
<script type="text/javascript">
import HomeHeader from './components/header'
import HomeSwiper from './components/swiper'
import HomeIcons from './components/icons'
import HomeRecommend from './components/recommend'
export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend
  }
}
</script>
<style lang="stylus" scoped>
</style>
