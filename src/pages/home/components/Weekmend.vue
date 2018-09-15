<template>
  <div>
    <p class="title">周末去哪</p>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="item-img-wrap">
          <img :src="item.imgUrl" alt="清凉你我他" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">
            {{item.title}}
          </p>
          <p class="item-desc">
            {{item.desc}}
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default{
  name: 'HomeWeekmend',
  props: {
    list: Array
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item
    overflow: hidden
    height: 4.05rem
    .item-img-wrap
      height: 0
      padding-bottom: 39%
      .item-img
        width: 100%
    .item-info
      padding: .1rem
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
</style>
