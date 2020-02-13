<template>
    <div>
      <city-header :cities="cities"></city-header>
      <city-list :hot="hot" :cities="cities" :letter="letter"></city-list>
      <city-alphabet :cities="cities" @change="infoFromAlpahbet"></city-alphabet>
    </div>
</template>

<script>
import CityHeader from './components/cityHeader'
import CityList from './components/list'
import CityAlphabet from './components/alphabet'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      hot: [],
      cities: {},
      letter: 100
    }
  },
  mounted () {
    this.getCityInfo()
  },
  methods: {
    getCityInfo () {
      axios.get('api/city.json').then(this.getCityInfoSucc)
    },
    getCityInfoSucc (res) {
      res = res.data
      if (res && res.ret) {
        var data = res.data
        this.hot = data.hotCities
        this.cities = data.cities
      }
    },
    infoFromAlpahbet (e) {
      this.letter = e
    }
  }
}
</script>

<style scoped>

</style>
