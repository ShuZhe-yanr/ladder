<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="current-city">
        <div class="title border-top" >当前城市</div>
        <div class="section-area">
            <div class="wrapper">
              <div class="city">北京</div>
            </div>
        </div>
      </div>
      <div class="hot-city">
        <div class="title border-top" >热门城市</div>
        <div class="section-area">
          <div class="wrapper" v-for="item of hot" :key="item.id">
            <div class="city">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="city-list" v-for="(item, key) of cities" :key="key" ref="key">
          <div class="title border-top" ref="title">{{key}}</div>
          <div v-for="itInfo of item" :key="itInfo.id">
            <div class="cities border-bottom">{{itInfo.name}}</div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'list',
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  props: {
    hot: Array,
    cities: Object,
    letter: {
      type: Number,
      dafault: 100
    }
  },
  watch: {
    letter () {
      if (this.letter !== 100) {
        const element = this.$refs.title[this.letter]
        console.log(this.$refs.title)
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .list
    overflow hidden
    position absolute
    top 1.7rem
    right 0
    left 0
    bottom 0
    .title
      height .86rem
      line-height .86rem
      background #f7f9fb
      text-indent 0.4rem
    .section-area
      overflow hidden
      padding 0 0.3rem
      padding-top 0.2rem
      .wrapper
        float left
        height 0.4rem
        line-height 0.4rem
        width 1.5rem
        border-radius 0.25rem
        padding 0.1rem
        margin 0 0.2rem
        margin-bottom 0.3rem
        background: rgba(255,150,69,0.1)
        .city
          font-size 0.28rem
          text-align center
          color #666
    .cities
      height .86rem
      line-height .86rem
      text-indent 0.4rem
</style>
