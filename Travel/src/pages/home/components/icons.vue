<template>
    <div class="icons">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(page, index) of pages" :key="index">
          <div class="icon" v-for="item of page" :key="item.id">
            <div class="icon-img">
              <img class="icon-img-content"  :src="item.pageUrl"/>
            </div>
            <span class="icon-content">{{item.content}}</span>
          </div>
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        autoPlay: false
      }
    }
  },
  props: {
    list: Array
  },
  computed: {
    pages () {
      var pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 10)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  .icons >>> .swiper-container
    height 0
    padding-bottom 50%
  .icon
    overflow hidden
    position relative
    float left
    height 0
    width 20%
    padding-bottom 25%
    //background indianred
    .icon-img
      position absolute
      top 0
      right 0
      bottom 0.44rem
      left 0
      box-sizing border-box
      padding 0.1rem
      //background lightgreen
      .icon-img-content
        display block
        margin-right auto
        margin-left auto
        margin-top 0.44rem
        height 60%
    .icon-content
      position absolute
      left 0
      right 0
      bottom 0
      height 0.44rem
      line-height 0.44rem
      text-align center
      color #333
</style>
