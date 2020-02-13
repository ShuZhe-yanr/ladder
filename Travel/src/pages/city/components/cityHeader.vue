<template>
    <div>
      <div class="header">城市选择</div>
      <div class="header-search">
        <span class="iconfont search-img">&#xe79e;</span>
        <input class="search-content" type="text" placeholder="位置 / 景点" v-model="keywords"/>
        <div class="search-cancel">取消</div>
      </div>
      <div class="search" v-show="keywords" ref="search">
        <ul>
          <li class="search-list" v-for="item of list" :key="item.id">{{item.name}}</li>
          <li class="search-list" v-show="haveData">没有找到相关城市</li>
        </ul>
      </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'cityHeader',
  props: {
    cities: Object
  },
  data () {
    return {
      keywords: '',
      list: [],
      timer: ''
    }
  },
  computed: {
    haveData () {
      return !this.list.length
    }
  },
  watch: {
    keywords () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keywords) > -1 || value.name.indexOf(this.keywords) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  }
}

</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    line-height .86rem
    font-size 0.32rem
    background $bgColor
    text-align center
    color #ffffff
  .header-search
    position relative
    height 0.66rem
    line-height 0.66rem
    padding 0.1rem
    padding-left 0.3rem
    background $bgColor
    .search-img
      position absolute
      left 0.38rem
      color #666
    .search-content
      float left
      font-size 0.32rem
      padding 0.07rem 0.5rem
      border-radius 0.5rem
      width 70%
    .search-cancel
      float left
      width 1.1rem
      font-size 0.3rem
      text-align center
      color #ffffff
  .search
    z-index 1
    overflow hidden
    position absolute
    top 1.7rem
    right 0
    left 0
    bottom 0
    background #eee
    .search-list
      line-height 0.62rem
      padding-left 0.2rem
      background #ffffff
      color #666
</style>
