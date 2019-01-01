<template>
	<div>
		<router-link tag="div" to="/" class="header-abs" v-show="showAbs">
			<div class="iconfont back-icon">&#xe624;</div>
		</router-link>
		<div class="header-fixed" v-show="!showAbs" :style="{opacity: this.opacityScroll}">
			景点详情
			<router-link to="/">
				<div class="iconfont back-icon">&#xe624;</div>
			</router-link>
		</div>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'DetailHeader',
		data () {
			return {
				showAbs: true,
				opacityScroll: 0
			}
		},
		methods: {
			handleScroll () {
				let top = document.documentElement.scrollTop
				console.log(top)
				if (top > 60) {
					this.showAbs = false
					let temp = top / 140
					this.opacityScroll = temp > 1 ? 1 : temp
				} else {
					this.showAbs = true
				}
			}
		},
		activated () {
			window.addEventListener('scroll', this.handleScroll)
		},
		deactivated () {
			window.removeEventListener('scroll', this.handleScroll)
		}
	}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
	.header-abs
		position absolute
		top .2rem
		left .2rem
		width .8rem
		height .8rem
		border-radius .4rem
		background-color rgba(0, 0, 0, .8)
		line-height .8rem
		text-align center
		.back-icon
			color #fff
	.header-fixed
		z-index 1
		position fixed
		top 0
		left 0
		right 0
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