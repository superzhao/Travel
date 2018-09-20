<template lang="html">
  <div>
    <detail-banner/>
    <detail-header/>
    <detail-list :list="list"/>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  data () {
    return {
      list: [
        {
          title: '中秋活动票',
          children: [
            {
              title: '大学生票'
            },
            {
              title: '[夜场]成人票'
            },
            {
              title: '三馆联票',
              children: [
                {
                  title: '三馆联票-馆一'
                },
                {
                  title: '三馆联票-馆二'
                },
                {
                  title: '三馆联票-馆三'
                }
              ]
            }
          ]
        },
        {
          title: '全价票'
        },
        {
          title: '优惠票',
          children: [
            {
              title: '儿童票'
            },
            {
              title: '老人票'
            }
          ]
        },
        {
          title: '一日游'
        }
      ]
    }
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  }
}
</script>

<style lang="css">
</style>
