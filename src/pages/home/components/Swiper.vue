<template>
  <div class="wrapper">
    <swiper :options="swiperOption"  v-if="showSwiper">
      <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="" >
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>

</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data() {
    return{
      swiperOption: {
        pagination: '.swiper-pagination',
        loop:true
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>
<style lang="stylus" scoped>//scoped 使样式名只作用于当前文件
  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff //这个属性是用来更改轮播图上小圆点颜色的。因为style添加了scoped只作用于本文件。所以要加>>>表示穿透。这样才能使属性设置成功
  .wrapper  //这个类的作用是在图片还没加载出来前就撑开图片位置的宽高。避免图片未加载时，下方的内容先顶在图片上，图片加载出来后再回退造成的问题
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 31.25%
    .swiper-img
      width: 100%
</style>
