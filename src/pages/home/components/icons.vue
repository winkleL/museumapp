<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icon-img">
            <img
              class="icon-img-content"
              :src="item.imgUrl"
              alt
            />
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {

  name: "HomeIcons",
  props:["list"],
  data() {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed:{
      pages(){
          const pages=[];
          this.list.forEach((item,index)=>{
              const page=Math.floor(index/8);
              if(!pages[page]){
                  pages[page]=[]
              }
              pages[page].push(item);
          })
          return pages
      }
  }
};
</script>
<style lang="stylus" scope>
@import '~styles/varibles.styl';
.icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
.icons {
  margin-top: 0.1rem;
  .icon {
    padding-bottom: 25%;
    width: 25%;
    float: left;
    position: relative;
    height: 0;
    overflow:hidden
    .icon-img {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.44rem;
      box-sizing: border-box;
      padding: 0.1rem;

      .icon-img-content {
        display: block;
        margin: 0 auto;
        height: 100%;
      }
    }

    .icon-desc {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 0.44rem;
      line-height: 0.44rem;
      color: $darkTextColor;
      text-align: center;
    }
  }
}
</style>