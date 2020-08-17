<template>
  <div>
    <banner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"/>
    <detail-header/>
    <div class="content">
    <detai-list :list="list" />
    </div>
  </div>
</template>

<script>
import banner from "./components/banner.vue";
import DetailHeader from "./components/header.vue";
import DetaiList from "./components/list.vue"
import axios from "axios" 
export default {
  name: "Detail",
  data() {
    return {
      sightName:"",
      bannerImg:"",
      gallaryImgs:[],
      list:[]
    };
  },
  components: {
    banner,
    DetailHeader,
    DetaiList
  },

  computed: {},

  mounted() {
    this.getDetailInfor()
  },

  methods: {
    getDetailInfor(){
      axios.get('api/detail.json?',{
        params:{
          id:this.$route.params.id
        }
      }).then(this.getDetailInforSucc)
    },
    getDetailInforSucc(res){
      res=res.data;
      if(res.ret && res.data){
        const data=res.data;
        this.sightName=data.sightName;
        this.list=data.categoryList;
        this.bannerImg=data.bannerImg;
        this.gallaryImgs=data.gallaryImgs;
        //console.log(data);
      }
    }
  },
};
</script>
<style lang="stylus" scoped></style>