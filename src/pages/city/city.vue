<template>
  <div>
    <city-header></city-header>
    <city-search :clist="cities"></city-search>
    <city-list :hclist="hotCities" :clist="cities" :letterDirec="letter"></city-list>
    <city-alphabet :clist="cities" @change="handleAphabet"></city-alphabet>
  </div>
</template>
<script type="text/javascript">
  import axios from 'axios'
  import CityHeader from './components/header'
  import CitySearch from './components/search'
  import CityList from './components/list'
  import CityAlphabet from './components/alphabet'
  export default {
    name: 'City',
    data () {
      return {
        cities: {},
        hotCities: [],
        letter: ''
      }
    },
    components: {
      CityHeader,
      CitySearch,
      CityList,
      CityAlphabet
    },
    methods: {
      getCityInfo () {
        axios.get('/api/city.json')
          .then(this.getCityInfoSucc)
      },
      getCityInfoSucc (res) {
        res = res.data
        if (res.ret && res.data) {
          const data = res.data
          this.cities = data.cities
          this.hotCities = data.hotCities
        }
      },
      handleAphabet (letter) {
        this.letter = letter
      }
    },
    mounted () {
      this.getCityInfo()
    }
  }
</script>
<style lang="stylus" scoped>
</style>
