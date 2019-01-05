<template>
	<div>
		<detail-banner :bannerImg="bannerImg" :gallaryImgs="gallaryImgs" :sightName="sightName"></detail-banner>
		<detail-header></detail-header>
		<div class="content">
			<detail-list :list="categoryList"></detail-list>
		</div>
	</div>
</template>
<script type="text/javascript">
	import DetailBanner from './components/banner'
	import DetailHeader from './components/header'
	import DetailList from './components/list'
	import axios from 'axios'
	export default {
		name: 'Detail',
		data () {
			return {
				sightName: '',
				bannerImg: '',
				gallaryImgs: [],
				categoryList: []
			}
		},
		components: {
			DetailBanner,
			DetailHeader,
			DetailList
		},
		methods: {
			getDetailInfo () {
				axios.get('/api/detail.json', {
					params: {
						id: this.$route.params.id
					}
				}).then(this.getDetailInfoSucc)
			},
			getDetailInfoSucc (res) {
				res = res.data
				if (res.ret && res.data) {
					const data = res.data
					this.sightName = data.sightName
					this.bannerImg = data.bannerImg
					this.gallaryImgs = data.gallaryImgs
					this.categoryList = data.categoryList
				}
			}
		},
		mounted () {
			this.getDetailInfo()
		}
	}
</script>
<style lang="stylus" scoped>
	.content
		height 50rem
</style>