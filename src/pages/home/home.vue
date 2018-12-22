<template>
	<div>
		<home-header></home-header>
  	<home-swiper></home-swiper>
  	<div>你好</div>
	</div>
</template>
<script type="text/javascript">
import HomeHeader from './components/header'
import HomeSwiper from './components/swiper'
export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeSwiper
  }
}
</script>
<style lang="stylus" scoped>
</style>
