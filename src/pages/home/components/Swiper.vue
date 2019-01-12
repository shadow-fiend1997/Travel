<template>
  <div class="wrapper">
    <swiper :options="swiperOption" >
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="" >
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>

</template>

<script>
export default {
  name: 'HomeSwiper',
  data() {
    return{
      swiperOption: {
        pagination: '.swiper-pagination',
        loop:true
      },
      swiperList: [{
        id: '0001',
        imgUrl:'http://img1.qunarzz.com/piao/fusion/1812/d6/daa880b254940402.jpg_750x200_b114308a.jpg'
      },{
        id: '0002',
        imgUrl:'http://img1.qunarzz.com/piao/fusion/1811/7c/8e5c4ab8ee8b7402.jpg_750x200_dd7a38dd.jpg'
      }]
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
