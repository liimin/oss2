<template>
    <!-- swiper -->
    <swiper :options="swiperOption" ref="mySwiper" class="my-swiper" >
      <swiper-slide v-for="(slide,index) in slides" :key="index"><a><img :src="slide.img_path" alt="" width="136" height="136"></a><h3>{{slide.title}}</h3></swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
      <div class="swiper-scrollbar"   slot="scrollbar"></div>
    </swiper>
</template>

<script>
import { mapGetters } from 'vuex'
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'dashboard',
  components: {
    swiper,
    swiperSlide
  },
  computed: {
    ...mapGetters([
      'name',
      'roles'
    ]),
    swiper() {
      return this.$refs.mySwiper.swiper
    }
  },
  data() {
    return {
      slides: [],
      swiperOption: {
        slidesPerView: 4,
        slidesPerColumn: 2,
        slidesPerGroup: 4,
        spaceBetween: 40,
        loopFillGroupWithBlank: true,
        // slidesPerColumnFill: 'row',
        // effect: 'coverflow',
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
          // type: 'progressbar',
          renderBullet: (index, className) => {
            return `<span class="${className}">${index + 1}</span>`
          }
        },
        keyboard: true,
        mousewheel: true,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        },
        scrollbar: {
          el: '.swiper-scrollbar'
        }
      }
    }
  },
  mounted() {
    for (let index = 0; index < 20; index++) {
      this.slides.push({
        img_path: 'http://www.qqw21.com/article/UploadPic/2014-6/20146301124368189.gif',
        title: `流量管理平台${index + 1}.0`
      }
      )
    }
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
.dashboard {
  &-container {
    margin-left: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
.swiper-container {
    height: auto!important;
    margin-left: auto;
    margin-right: auto;
    padding: 40px 20px;
    .swiper-scrollbar {
      top: 0;
      height: 2px;
    }
  .swiper-slide {
    height: 200px;
    text-align: center;
    a img{
      border-style: none;
      border-radius: 30px;
      //padding: 20px;
      box-shadow: 0 6px 30px #ccc;
      margin-bottom: 15px
    }
    h3{
      font-size: 14px;
      font-family: 微软雅黑;
      color: #41464a;
    }
  }
}
</style>
<style>
 .my-swiper .swiper-pagination-bullet {
    width: 20px;
    line-height: 20px;
    height: 20px;
    color: #fff;
    box-shadow: 0px 2px 1px #666 inset, 2px 3px 4px #666;
    font-size: 12px ;
}
.my-button-disabled{
  opacity: .3
}
</style>

