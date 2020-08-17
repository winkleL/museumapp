<template>
  <div style="">
    <div class="title">热展推荐</div>
    <ul>
        <router-link 
          class="item border-bottom" 
          v-for="item of list" 
          :key="item.id" 
          tag="li"
          :to="'/detail/'+item.id"
        >
            <img :src="item.imgUrl" class="item-img">
            <div class="item-infor">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
                <button class="item-btn">查看详情</button>
            </div>
        </router-link>
    </ul>
  </div>
</template>

<script>
export default {
    name:'RecommendIcons',
    props:["list"]
}

</script>
<style lang="stylus" scoped >
@import '~styles/mixins.styl'
.title
  margin-top .2rem
  line-height .8rem
  background #cfccc9
  text-indent .2rem
.item
  height 1.9rem
  display flex
  
  .item-img
    width 1.7rem
    height 1.7rem 
    padding .1rem
  .item-infor
    flex 1
    padding .1rem
    min-width 0
    .item-title
      line-height .54rem
      font-size .32rem
      ellipsis()
    .item-desc 
      line-height .4rem
      color #666
      ellipsis()
    .item-btn
      background #d4c4b7
      padding 0 0.1rem
      margin-top .2rem
      border-radius .06rem
</style>