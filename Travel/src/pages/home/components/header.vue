<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont icon-left">&#xe789;</div>
    </div>
    <div class="header-input">
      <span class="iconfont icon-input">&#xe79e;</span>
      输入城市 / 景点 / 游玩主题
    </div>
    <router-link to="././city/City" >
      <div class="header-right">
        {{city}}
        <span class="iconfont icon-right">&#xe78e;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
    .header
      display flex
      line-height:.86rem
      background $bgColor
      color #fff
      .header-left
        width:.64rem
        float:left
        .icon-left
          //text-align center
          font-size .4rem
          padding-left .2rem
      .header-input
        flex: 1
        height .62rem
        line-height .62rem
        margin-top .12rem
        //margin-bottom .12rem
        margin-left .2rem
        background #ffffff
        border-radius .1rem
        color #ccc
        .icon-input
          padding-left .2rem
      .header-right
        width: 1.24rem
        float: right
        text-align center
        color #ffffff
        .icon-right
          margin-left -0.056rem
          font-size .25rem
</style>
