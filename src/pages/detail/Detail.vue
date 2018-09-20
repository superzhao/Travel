<template lang="html">
  <div>
    <detail-banner :bannerImg="bannerImg" :sightName="sightName" :gallaryImgs="gallaryImgs"/>
    <detail-header :imgs="gallaryImgs"/>
    <detail-list :list="list"/>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  data () {
    return {
      list: [],
      bannerImg: '',
      gallaryImgs: [],
      sightName: ''
    }
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  mounted () {
    this.getDetailInfo()
  },
  methods: {
    getDetailInfo () {
      // axios.get('/api/detail.json:id='+this.$route.params.id)
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      })
        .then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      if (res.data.ret && res.data.data) {
        const data = res.data.data
        this.list = data.categoryList
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.sightName = data.sightName
      }
    }
  }
}
</script>

<style lang="css">
</style>
