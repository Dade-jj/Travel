<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe600;</div>
    </router-link>
    <div class="header-fixed" :style="opacityStyle" v-show="!showAbs">
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe600;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.header-abs
  position: absolute
  top: .2rem
  left: .2rem
  height: .8rem
  line-height: .8rem
  width: .8rem
  border-radius: .4rem
  background: rgba(0, 0, 0, .8)
  .header-abs-back
    text-align: center
    color: #fff
    font-size: .4rem
.header-fixed
  position: fixed
  overflow: hidden
  top: 0
  left: 0
  right: 0
  height: $headerHeight
  line-height: $headerHeight
  text-align: center
  color: #fff
  background: $bgColor
  font-size: .32rem
  .header-fixed-back
    position: absolute
    top: 0
    left: 0
    width: .64rem
    font-size: .4rem
    text-align: center
    color: #fff
</style>
