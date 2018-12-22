<template>
	<div>
		<div class="title">热销推荐</div>
		<ul>
			<li class="item border-bottom" v-for="item of recommendList" :key="item.id">
				<img class="item-img" :src="item.imgURL">
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</li>
		</ul>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'HomeRecommend',
		data () {
			return {
				recommendList: [
					{
						id: '0001',
						imgURL: 'http://img1.qunarzz.com/sight/p0/1412/9f/fbff2a5302c0ce906ef9b64159730f89.water.jpg_250x250_0130a49d.jpg',
						title: '上海海洋水族馆上海海洋水族馆上海海洋水族馆上海海洋水族馆',
						desc: '亲眼见证鲨鱼的恐怖亲眼见证鲨鱼的恐怖亲眼见证鲨鱼的恐怖'
					},
					{
						id: '0002',
						imgURL: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
						title: '上海迪士尼乐园上海迪士尼乐园上海迪士尼乐园上海迪士尼乐园',
						desc: '全球最大的迪士尼城堡全球最大的迪士尼城堡全球最大的迪士尼城堡'
					},
					{
						id: '0003',
						imgURL: 'http://img1.qunarzz.com/sight/p0/1502/ba/ba5f873a22327e0f.water.jpg_200x200_9bf5cc14.jpg',
						title: '上海影视乐园上海影视乐园上海影视乐园',
						desc: '小伙伴们都收藏了，去看看吧~小伙伴们都收藏了，去看看吧~'
					},
					{
						id: '0004',
						imgURL: 'http://img1.qunarzz.com/sight/p0/1411/4f/146031f0bc5d7e0dd960d3f5bf0c9eca.water.jpg_200x200_f22705c9.jpg',
						title: '上海科技馆',
						desc: '技术改变生活，只有想不到没有做不到技术改变生活，只有想不到没有做不到'
					}
				]
			}
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