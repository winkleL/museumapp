<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div 
            class="button-wrapper" 
            v-for="item of hotcities" 
            :key="item.id"
            @click="handleCityClick(item.name)"
            >
            <div class="button" >{{item.name}}</div>
          </div>
        </div>
      </div>
      <div 
        class="area" 
        v-for="(item,key) of cities" 
        :key="key"
        :ref="key"
      >
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list" >
          <div class="item border-bottom" v-for="c of item" :key="c.id" @click="handleCityClick(c.name)">{{c.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
import { mapState , mapMutations } from "vuex"
export default {
  name: "CityList",
  props:["cities","hotcities","letter"],
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper);
  },
  methods:{
    handleCityClick(city){
      //this.$store.commit("changeCity",city);
      this.changeCity(city)
      this.$router.push("/");
    },
    ...mapMutations(['changeCity'])
  },
  watch:{
    letter(){
      if(this.letter){
        const element=this.$refs[this.letter][0];
        this.scroll.scrollToElement(element)
      }
    }
  },
  computed:{
    ...mapState(['city'])
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'

.border-topbottom
  &:before
    border-color #ccc
  &:after
    border-color #ccc
.border-bottom
  &:before
    border-color #ccc
.list
  position absolute
  top 1.58rem
  left 0
  bottom 0
  right 0
  overflow hidden
  .title
    line-height 0.54rem
    background #eee
    padding-left 0.2rem
    color #666
    font-size 0.26rem
  .button-list
    padding 0.1rem 0.6rem 0.1rem 0.1rem
    overflow hidden
    .button-wrapper
      width 33.33%
      float left
      .button
        margin 0.1rem
        padding 0.1rem 0
        text-align center
        border 0.02rem solid #ccc
        border-radius 0.06rem
  .item-list
    line-height 0.76rem
    padding 0.2rem
</style>
