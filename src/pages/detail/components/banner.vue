<template>
	<div>
		<div class="banner" @click="handleBanner">
			<img class="banner-img" :src="bannerImg">
			<div class="banner-info">
				<div class="banner-number">
					<span class="iconfont banner-icon">&#xe692;&nbsp;</span>
					<em>{{this.gallaryImgs.length}}</em>
				</div>
				<div class="banner-title">{{this.sightName}}</div>
			</div>
		</div>
		<common-fade>
			<common-gallary :images="gallaryImgs" v-show="showGallary" @close="handleGallary"></common-gallary>
		</common-fade>
	</div>
</template>
<script type="text/javascript">
	import CommonGallary from 'common/gallary/gallary'
	import CommonFade from 'common/fade/fade'
	export default {
		name: 'DetailBanner',
		props: {
			sightName: String,
			bannerImg: String,
			gallaryImgs: Array
		},
		data () {
			return {
				showGallary: false
			}
		},
		methods: {
			handleBanner () {
				this.showGallary = true
			},
			handleGallary () {
				this.showGallary = false
			}
		},
		components: {
			CommonGallary,
			CommonFade
		}
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