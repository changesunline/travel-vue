<template>
  <ul class="list">
    <li class="item" v-for="key of letters" :key="key" :ref="key" @click="letterClick" @touchstart.prevent="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd">
      {{key}}
    </li>
  </ul>
</template>
<script type="text/javascript">
  export default {
    name: 'CityAlphabet',
    props: {
      clist: Object
    },
    data () {
      return {
        touchStatus: false,
        startY: 0,
        timer: null
      }
    },
    updated () {
      // startY是A到当前父元素顶部的距离
      this.startY = this.$refs['A'][0].offsetTop
    },
    computed: {
      letters () {
        let letters = []
        for (let key in this.clist) {
          letters.push(key)
        }
        return letters
      }
    },
    methods: {
      letterClick (e) {
        this.$emit('change', e.target.innerText)
      },
      letterBiger () {
        for (let key of this.letters) {
          this.$refs[key][0].style.cssText = 'line-height:.4rem'
        }
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
            // touchY返回触点相对于可见视区(visual viewport)上边沿的的Y坐标
            const touchY = e.touches[0].clientY
            // 79是header+search组件的总高度1.58*50，20是每个字母所在元素item的高度
            const index = Math.floor((touchY - this.startY - 79) / 20)
            if (index >= 0 && index < this.letters.length) {
              this.$emit('change', this.letters[index])
              const currentDom = this.$refs[this.letters[index]][0]
              // 滑动字母表字体放大的功能
              this.letterBiger()
              currentDom.style.cssText = 'line-height:.5rem; font-size:.4rem'
            }
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
  @import '~styles/varibles.styl'
  .list
    display flex
    flex-direction column
    justify-content center
    position absolute
    top 1.58rem
    right 0
    bottom 0
    width .4rem
    .item
      text-align center
      line-height .4rem
      color $bgColor
</style>