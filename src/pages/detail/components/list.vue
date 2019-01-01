<template>
	<div>
		<div v-for="(item, index) of list" :key="index">
			<div class="item-title border-bottom">
				<span class="item-title-icon"></span>
				{{item.title}}
			</div>
			<div v-if="item.children" class="item-children">
				<detail-list :list="item.children"></detail-list>
			</div>
		</div>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'DetailList',
		props: {
			list: Array
		}
	}
</script>
<style lang="stylus" scoped>
	.item-title
		position relative
		line-height .8rem
		font-size .32rem
		padding 0 .4rem
		margin .2rem
	.item-title-icon
		position absolute
		left 0
		top .2rem
		display: inline-block
		width .36rem
		height .36rem
		background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
		background-size .4rem 3rem
	.item-children
		padding 0 .2rem
</style>