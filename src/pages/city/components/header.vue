<template>
	<div class="header">
		城市选择
		<router-link to="/">
			<div class="iconfont back-icon">&#xe624;</div>
		</router-link>
	</div>
</template>
<script type="text/javascript">
	export default {
    name: 'CityHeader'
  }
</script>
<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		overflow hidden
		height $headerHeight
		background-color $bgColor
		text-align center
		line-height $headerHeight
		color #fff
		font-size .32rem
		.back-icon
			position absolute
			top 0
			left 0
			width .64rem
			text-align center
			font-size .4rem
			color #fff
</style>