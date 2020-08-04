<template>
  <div class="wrapper">
    <swiper :options="swiperOptions">
    <swiper-slide v-for="item of list" :key="item.id"><img class="swiper-img" :src="item.imgUrl" alt=""></swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
  </div>
</template>

<script>
export default {
    name:'HomeSwiper',
    props:["list"],
    data(){
        return {
            swiperOptions:{
                pagination:'.swiper-pagination'
            }
        }
    }
}

</script>
<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
  background-color: #fbeee2
.wrapper
  overflow:hidden
  .swiper-img 
    height:3rem
    width:100%
</style>