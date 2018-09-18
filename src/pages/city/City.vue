<template>
  <div>
    <city-header/>
    <city-search/>
    <city-list :cities="this.cities" :hotCities="this.hotCities" :curLetter="this.curLetter"/>
    <city-alphabet :cities="this.cities" @letterChange="handleLetterChange"/>
  </div>
</template>
<script>
import axios from 'axios'
import CityHeader from './components/header'
import CitySearch from './components/search'
import CityList from './components/list'
import CityAlphabet from './components/Alphabet'
export default{
  name: 'City',
  data () {
    return {
      cities: {},
      hotCities: [],
      curLetter: ''
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
      axios.get('/static/jsons/city.json')
        .then(
          this.getCityInfoSucc
        )
    },
    getCityInfoSucc (res) {
      if (res.data.ret && res.data.data) {
        const data = res.data.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    handleLetterChange (letter) {
      this.curLetter = letter
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>
<style lang="stylus" scoped>

</style>
