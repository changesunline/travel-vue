<template>
	<div>
		<home-header></home-header>
  	<home-swiper></home-swiper>
  	<home-icons></home-icons>
	</div>
</template>
<script type="text/javascript">
import HomeHeader from './components/header'
import HomeSwiper from './components/swiper'
import HomeIcons from './components/icons'
export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons
  }
}
</script>
<style lang="stylus" scoped>
</style>
