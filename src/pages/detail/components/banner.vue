<template>
	<div class="banner">
		<img class="banner-img" src="//img1.qunarzz.com/sight/p0/1412/9f/fbff2a5302c0ce906ef9b64159730f89.water.jpg_600x330_b9a742ef.jpg">
		<div class="banner-info">
			<div class="banner-number">
				<span class="iconfont banner-icon">&#xe692;&nbsp;</span>
				<em>11</em>
			</div>
			<div class="banner-title">上海海洋水族馆(AAAA景区)</div>
		</div>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'DetailBanner'
	}
</script>
<style lang="stylus" scoped>
	.banner
		position relative
		overflow hidden
		height 0
		padding-bottom 55%
		background-color #ccc
		.banner-img
			width 100%
		.banner-info
			position absolute
			left 0
			right 0
			bottom 0
			color #fff
			background-image linear-gradient(top, rgba(0, 0, 0 ,0), rgba(0, 0, 0, .8))
			.banner-title
				color #fff
				padding .2rem 0 .3rem .2rem
				font-size .32rem
			.banner-number
				margin-left .2rem
				width 1.2rem
				height .4rem
				line-height .4rem
				background-color rgba(0, 0, 0, .5)
				text-align center
				font-size .24rem
				border-radius .2rem
				.banner-icon
					font-size .24rem
</style>