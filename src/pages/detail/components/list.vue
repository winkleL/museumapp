<template>
  <div>
    <div class="item" v-for="(item,index) of list" :key="index">
      <div class="item-title border-bottom">
        <span class="item-title-icon iconfont"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "DetailList",
  props: ["list"],
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.item-title-icon
 background url("../../../assets/img/文物收藏.png") 0 0 no-repeat
 background-size cover
 display inline-block
 width .36rem
 height .36rem
.item-title
  line-height .8rem
  font-size .32rem
  padding 0 .2rem
.item-children
  padding 0 .1rem  

</style>