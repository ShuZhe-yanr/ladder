<template>
  <ul class="al-area">
    <li class="alphabet"
        v-for="item of letters"
        :key="item"
        ref="alphabet"
        @touchstart="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        @click="handleGetInfo"
    >{{item}}</li>
  </ul>
</template>

<script>
export default {
  name: 'alphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      timer: null
    }
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
    handleGetInfo (e) {
      var str = e.target.innerText
      var letter = str.charCodeAt() - 65
      this.$emit('change', letter)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const first = this.$refs.alphabet[0].offsetTop
          const courrent = e.touches[0].clientY - 85.4
          const num = Math.floor((courrent - first) / 20)
          this.$emit('change', this.letters[num].charCodeAt() - 65)
          console.log(this.letters[num].charCodeAt() - 65)
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles'
  .al-area
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .alphabet
      line-height: .4rem
      text-align: center
      color: $bgColor
</style>
