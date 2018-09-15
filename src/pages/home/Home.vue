<template>
  <div>
    <HomeHeader/>
    <home-swiper/>
    <home-icons/>
    <home-recommend/>
    <home-weekmend/>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekmend from './components/Weekmend'

export default{
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekmend
  }
}
</script>
<style>
</style>
