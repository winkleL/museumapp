<template>
  <div class="app">
    <home-header/>
    <home-swiper :list="swiperList"/>
    <home-icons :list="iconList"/>
    <recommend-icons :list="recommendList"/>
  </div>
</template>

<script>
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/swiper.vue'
import HomeIcons from './components/icons.vue'
import RecommendIcons from './components/recom.vue'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
  name: 'Home',
  data(){
    return {
      swiperList:[],
      iconList:[],
      recommendList:[],
      lastCity:''
    }
  },
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    RecommendIcons
  },
  methods:{
    getHomeInfor(){
      axios.get('/api/index.json?city='+this.city)
           .then(this.getHomeInforSucc)
    },
    getHomeInforSucc(res){
      res=res.data;
      if(res.ret&&res.data){
        const data=res.data;
        // this.city=data.city;
        this.swiperList=data.swiperList;
        this.iconList=data.iconList;
        this.recommendList=data.recommendList;
      }
    }
  },
  mounted(){
    this.getHomeInfor()
    this.lastCity=this.city;
  },
  computed:{
    ...mapState(['city'])
  },
  activated(){
    if(this.lastCity!==this.city){
      this.getHomeInfor();
      this.lastCity=this.city
    }
  }
}
</script>

