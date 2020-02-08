<template>
    <div>
      <div class="title">周末去哪</div>
      <ul>
        <li class="item border-bottom" v-for="item of list" :key="item.id">
          <div class="item-img-content">
            <img class="item-img" :src="item.imgUrl"/>
          </div>
          <div class="item-content">
            <p class="item-content-title">{{item.title}}</p>
            <p class="item-content-desc">{{item.desc}}</p>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'weakend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .title
    margin-top 0.2rem
    height 0.8rem
    line-height 0.8rem
    background #eee
    text-indent 0.2rem
  .item-img-content
    height 0
    padding-bottom 37.32%
    .item-img
      width 100%
      padding-top 0.1rem
  .item-content
    padding 0.2rem
    .item-content-title
      line-height 0.54rem
      font-size 0.34rem
    .item-content-desc
      line-height 0.42rem
      font-size 0.24rem
      color #616161
      padding-right 1.4rem
      overflow hidden
      white-space nowrap
      text-overflow ellipsis
</style>
