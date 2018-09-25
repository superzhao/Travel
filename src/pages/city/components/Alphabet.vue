<template>
  <ul class="list">
      <li
        class="item"
        v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
      >
        {{item}}
      </li>
  </ul>
</template>
<script>
export default{
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchSatus: false,
      startY: ''
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('letterChange', e.target.innerText)
    },
    handleTouchStart (e) {
      this.touchSatus = true
    },
    handleTouchMove (e) {
      if (this.touchSatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index <= this.letters.length) {
            this.$emit('letterChange', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd (e) {

    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .list
    display:flex
    flex-direction:column
    justify-content:center
    position:absolute
    top:1.58rem
    right:0
    bottom:0
    width:.4rem
    .item
      height:.4rem
      line-height: .4rem;
      text-align:center
      color:$bgColor
    .active
      color:#fff
      background:$bgColor
      border-radius:50%
</style>
