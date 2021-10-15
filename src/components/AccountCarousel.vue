<template>
  <div class="hello">
    <swiper 
      ref="accountCarousel" 
      :options="carouselOptions"
    >
      <swiper-slide>Slide 1</swiper-slide>
      <swiper-slide>Slide 2</swiper-slide>
      <swiper-slide>Slide 3</swiper-slide>
      <swiper-slide>Slide 4</swiper-slide>
      <swiper-slide>Slide 5</swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  name: 'AccountCarousel',
  data() {
    return {
      carouselOptions: {
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
        },
        spaceBetween: 20,
        grabCursor: true,
        slidesPerView: 3,
        centeredSlides: true,
        keyboard: {
          enabled: true,
          onlyInViewport: false,
        },
      }
    }
  },
  components: {
    Swiper,
    SwiperSlide
  },
  computed: {
    swiper() {
      return this.$refs.accountCarousel.$swiper
    }
  },
  mounted() {
    console.log('Current Swiper instance object', this.swiper)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.swiper-container {
  height: 300px;
}

.swiper-slide {
  border: 1px solid black;
  transition: all .2s;
  height: 220px;
  margin-top: 15px;
}

.swiper-slide-active {
  height: 250px;
  margin-top: 0;
}
</style>
