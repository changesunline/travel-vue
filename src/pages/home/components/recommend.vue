<template>
	<div>
		<div class="title">热销推荐</div>
		<ul>
			<router-link tag="li" :to="'/detail/' + item.id"
			class="item border-bottom" v-for="item of List" :key="item.id">
				<img class="item-img" :src="item.imgUrl">
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</router-link>
		</ul>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'HomeRecommend',
		props: {
			List: Array
		}
	}
</script>
<style lang="stylus" scoped>
	@import '~styles/mixins.styl'
	.title
		line-height .6rem
		background-color #eee
		margin-top .2rem
		text-indent .2rem
	.item
		overflow hidden
		display flex
		height 2.1rem
		.item-img
			width 1.7rem
			height 1.7rem
			padding .2rem
		.item-info
			flex 1
			padding .2rem .2rem .2rem 0
			min-width 0
			.item-title
				line-height .54rem
				font-size .32rem
				ellipsis()
			.item-desc
				line-height .4rem
				color #fe4444
				ellipsis()
			.item-button
				background-color #ff9300
				line-height .3rem
				margin-top .2rem
				font-size .15rem
				padding .05rem .2rem
				border-radius .05rem
				color #fff
</style>