<template>
  <div>
    <router-link 
      tag="div" 
      to="/" 
      class="header-abs"
      v-show="showAbs"
    >
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div 
      class="header-fixed" 
      v-show="!showAbs"
      :style="opacityStyle"
    >
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      展览详情
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailHeader",
  data() {
    return {
        showAbs:true,
        opacityStyle:{
            opacity:0
        }
    }
  },
 
  methods:{
      handleScroll(){
          const top=document.documentElement.scrollTop;
          if(top>60){
              let opacity=top/140;
              opacity=opacity>1?1:opacity;
              console.log(opacity)
              this.opacityStyle={opacity};
              this.showAbs=false;
          }else{
              this.showAbs=true;
          }
          console.log(top)
      }
  },
  mounted(){
      window.addEventListener('scroll',this.handleScroll)
  },
  unmounted() {
    window.removeEventListener('scroll',this.handleScroll)
  },
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'

.header-abs
  position absolute
  top 0.2rem
  left 0.2rem
  width 0.8rem
  height 0.8rem
  border-radius 0.4rem
  background rgba(0, 0, 0, 0.6)
  text-align center
  line-height 0.8rem
  .header-abs-back
    color #fff
    font-size 0.4rem
.header-fixed
  z-index 2
  height $headerHeight
  line-height $headerHeight
  text-align center
  background $bgColor
  color #fff
  font-size 0.32rem
  position fixed
  top 0
  left 0
  right 0
  .header-fixed-back
    width 0.64rem
    text-align center
    font-size 0.4rem
    position absolute
    top 0
    left 0
    color #fff
</style>