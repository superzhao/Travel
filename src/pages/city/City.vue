<template>
  <div>
    <city-header/>
    <city-search/>
  </div>
</template>
<script>
import CityHeader from './components/header'
import CitySearch from './components/search'
export default{
  name: 'City',
  components: {
    CityHeader,
    CitySearch
  }
}
</script>
<style scoped>

</style>
