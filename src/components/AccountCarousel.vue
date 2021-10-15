<template>
  <div class="stage">
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
        spaceBetween: -8, // achieves the 15px gap between carousel slides as prescribed in final design
        grabCursor: true,
        slidesPerView: 'auto', // this combined with set width of carousel panes gives us the "peeking" effect
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
.stage {
  max-width: 376px;
  margin: 0 auto;
}

.swiper-container {
  height: 240px;
}

.swiper-slide {
  border: 1px solid black;
  transition: all .2s;
  height: 196px;
  width: 312px;
  transform: scale(0.9);
  background-color: white;
  border-radius: 10px;
}

.swiper-slide-active {
  margin-top: 0;
  transform: scale(1);
}

@media only screen and (max-width: 376px) {
  .stage {
    width: 100vw;
  }
}
</style>
