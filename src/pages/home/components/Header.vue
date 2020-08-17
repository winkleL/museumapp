<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/博物馆/文物
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe6aa;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: "HomeHeader",
  computed:{
    ...mapState(['city'])
  }
  
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.header {
  line-height: $headerHeight;
  background: $bgColor;
  display: flex;
  color: #fff;

  .header-left {
    width: 0.64rem;
    float: left;

    .back-icon {
      text-align: center;
      font-size: 0.4rem;
    }
  }

  .header-input {
    flex: 1;
    background: #fff;
    border-radius: 0.1rem;
    margin-top: 0.12rem;
    height: 0.64rem;
    line-height: 0.64rem;
    margin-left: 0.2rem;
    color: #ccc;
    padding-left: 0.2rem;
  }

  .header-right {
    min-width: 1.24rem;
    float: right;
    text-align: center;
    color:#fff;
    padding-left .1rem
    .arrow-icon {
      font-size: 0.24rem;
    }
  }
}
</style>
