<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">{{this.currentCity}}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="item of hclist" :key="item.id">
						<div class="button" @click="handleClick(item.name)">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="area" v-for="(val, key) of clist" :key="key" :ref="key">
				<div class="title border-topbottom">{{key}}</div>
				<div class="item-list">
					<div class="item border-bottom" v-for="item of val" :key="item.id" @click="handleClick(item.name)">{{item.name}}</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script type="text/javascript">
	import BScroll from 'better-scroll'
	import { mapState, mapMutations } from 'vuex'
  export default {
    name: 'CityList',
    props: {
    	clist: Object,
    	hclist: Array,
    	letterDirec: String
    },
    computed: {
    	...mapState({
    		currentCity: 'city'
    	})
    },
    methods: {
    	handleClick (city) {
    		this.changeCity(city)
    		this.$router.push('/')
    	},
    	...mapMutations(['changeCity'])
    },
    watch: {
    	letterDirec () {
    		if (this.letterDirec) {
    			const element = this.$refs[this.letterDirec][0]
    			this.scroll.scrollToElement(element)
    		}
    	}
    },
    mounted () {
    	this.scroll = new BScroll(this.$refs.wrapper, {
    		click: true
    	})
    }
  }
</script>
<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.border-topbottom
		&:before
			border-color #ccc
		&:after
			border-color #ccc
	.border-bottom
		&:before
			border-color #ccc
	.list
		position absolute
		top 1.58rem
		left 0
		right 0
		bottom 0
		overflow hidden
		.title
			line-height .54rem
			background-color #eee
			padding-left .2rem
		.button-list
			overflow hidden
			padding .2rem .6rem .2rem .2rem
			.button-wrapper
				float left
				width 33.3%
				.button
					margin .1rem
					padding .1rem
					border .02rem solid #aaa
					border-radius .06rem
					text-align center
		.item-list
			.item
				line-height .76rem
				padding-left .2rem
</style>
