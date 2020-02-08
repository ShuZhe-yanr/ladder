<template>
  <div>
    <div class="title">今日特惠</div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <img class="item-img" :src="item.imgUrl" />
        <div class="item-content">
          <p class="item-content-title">{{item.title}}</p>
          <p class="item-content-desc">{{item.desc}}</p>
          <button class="item-content-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'recommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl"
  .title
    margin-top 0.4rem
    line-height 0.8rem
    background #eee
    text-indent 0.2rem
  .item
    overflow hidden
    height 1.9rem
    display flex
    .item-img
      padding 0.1rem
      height 1.7rem
      width 2.6rem
      border-radius 0.2rem
    .item-content
      flex 1
      padding 0.1rem
      min-width 0
      .item-content-title
        line-height 0.54rem
        font-size 0.34rem
        ellipse()
      .item-content-desc
        line-height 0.4rem
        color #555
        ellipse()
      .item-content-button
        margin-top 0.2rem
        line-height 0.4rem
        font-size 0.25rem
        padding 0.1rem
        border-radius 0.1rem
        color white
        background #17c0c8
</style>
