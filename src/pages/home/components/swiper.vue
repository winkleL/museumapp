<template>
  <div class="wrapper">
    <swiper :options="swiperOptions">
    <swiper-slide v-for="item of swiperList" :key="item.id"><img class="swiper-img" :src="item.imgurl" alt=""></swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
  </div>
</template>

<script>
export default {
    name:'HomeSwiper',
    data(){
        return {
            swiperOptions:{
                pagination:'.swiper-pagination'
            },
            swiperList:[
                {
                    id:'0001',
                    imgurl:'https://img.dpm.org.cn/Uploads/Picture/2020/07/28/s5f1fe8978bf05.jpg'
                },
                {
                    id:'0002',
                    imgurl:'https://img.dpm.org.cn/Uploads/Picture/2020/07/31/s5f23afcc67ec3.jpg'
                }
            ]
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