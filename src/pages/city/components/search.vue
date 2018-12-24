<template>
	<div>
		<div class="search">
			<input v-model="keyWord" class="search-input" type="text" name="search" placeholder="输入城市名或拼音">
		</div>
		<div class="search-content" ref="wrapper" v-show="keyWord">
			<ul>
				<li class="search-item border-bottom" v-for="item of result" :key="item.id" @click="handleClick(item.name)">
					{{item.name}}
				</li>
				<li class="search-item border-bottom" v-show="hasNoData">没有更多数据</li>
			</ul>
		</div>
	</div>
</template>
<script type="text/javascript">
	import BScroll from 'better-scroll'
  export default {
    name: 'CitySearch',
    props: {
    	clist: Object
    },
    data () {
    	return {
    		keyWord: '',
    		timer: null,
    		result: []
    	}
    },
    computed: {
    	hasNoData () {
    		return !this.result.length
    	}
    },
    mounted () {
    	this.scroll = new BScroll(this.$refs.wrapper)
    },
    methods: {
        handleClick (city) {
          this.$store.commit('changeCity', city)
          this.$router.push('/')
        }
    },
    watch: {
    	keyWord () {
    		if (this.timer) {
    			clearTimeout(this.timer)
    		}
    		if (!this.keyWord) {
    			this.result = []
    			return
    		}
    		this.timer = setTimeout(() => {
    			const result = []
    			for (let key in this.clist) {
    				this.clist[key].forEach((item, index) => {
    					if (item.spell.indexOf(this.keyWord) > -1 ||
    						item.name.indexOf(this.keyWord) > -1) {
    						result.push(item)
    					}
    				})
    			}
    			this.result = result
    		}, 100)
    	}
    }
  }
</script>
<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.search
		height .72rem
		padding  0 .1rem
		background-color $bgColor
		.search-input
			box-sizing border-box
			width 100%
			height .62rem
			padding 0 .1rem
			line-height .62rem
			text-align center
			border-radius .06rem
			color #333
	.search-content
		z-index 1
		overflow hidden
		position absolute
		top 1.58rem
		left 0
		right 0
		bottom 0
		background-color #eee
		.search-item
			line-height .62rem
			padding-left .2rem
			background-color #fff
			color #666
</style>
