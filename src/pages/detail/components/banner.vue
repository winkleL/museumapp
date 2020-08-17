<template>
<div>
  <div class="banner" @click="handleGallary">
   <img class="banner-img" :src="bannerImg">
   <div class="banner-infor">
     <div class="banner-title">{{sightName}}</div>
     <div class="banner-number"><span class="iconfont">&#xe67c;</span>  {{gallaryImgs.length}}</div>
   </div>
  </div>
  <common-fade>
  <common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="handleGallaryClose"/>
  </common-fade>
</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import CommonFade from 'common/fade/fade'
export default {
  name:"DetailBanner",
  props:['sightName','bannerImg','gallaryImgs'],
  components:{
      CommonGallary,
      CommonFade
     
  },
  data () {
    return {
        showGallary:false
    };
  },

  computed:{},

  mounted(){},

  methods: {
      handleGallary(){
          this.showGallary=true
      },
      handleGallaryClose(){
          this.showGallary=false
      }
  }
}

</script>
<style lang="stylus" scoped>
.banner
  overflow hidden
  height 0
  padding-bottom 55%
  position relative
  .banner-img
    width 100%
  .banner-infor
    position absolute
    line-height .6rem
    left 0
    right 0
    bottom 0
    display flex
    color #fff
    background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.6))
    .banner-title
      flex 1
      font-size .36rem
      padding 0 .2rem
    .banner-number
      padding 0 .4rem
      height .32rem
      line-height .32rem
      border-radius .2rem
      border .01rem solid #fff
      margin-top .1rem
</style>