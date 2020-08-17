<template>
  <div>
    <city-header/>
    <city-search :cities="cities"/>
    <city-list :cities="cities" :hotcities="hotcities" :letter="letter"/>
    <city-alphabet :cities="cities" @change="handleLetterChange"/>
  </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header.vue'
import CitySearch from './components/search.vue'
import CityList from './components/list.vue'
import CityAlphabet from './components/Alphabet.vue'
export default {
  name:'City',
  data(){
    return {
      hotcities:[],
      cities:{},
      letter:''
    }
  },
  components:{
      CityHeader,
      CitySearch,
      CityList,
      CityAlphabet
  },
  methods:{
    getCityInfor(){
      axios.get('/api/city.json').then(this.handleGetCityInforSucc)
    },
    handleGetCityInforSucc(res){
      res=res.data;
      if(res.ret && res.data){
        const data=res.data;
        this.hotcities=data.hotCities;
        this.cities=data.cities;
      }
    },
    handleLetterChange(letter){
      this.letter=letter;
    }
  },
  mounted(){
    this.getCityInfor();
  }
}
</script>
<style lang="stylus" scoped>
</style>