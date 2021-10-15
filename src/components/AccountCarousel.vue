<template>
  <div class="stage">
    <swiper 
      ref="accountCarousel" 
      :options="carouselOptions"
    >
      <swiper-slide>Account 1</swiper-slide>
      <swiper-slide>Account 2</swiper-slide>
      <swiper-slide>Account 3</swiper-slide>
      <swiper-slide>Account 4</swiper-slide>
      <swiper-slide>Account 5</swiper-slide>
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
/** SWIPER STYLES **/

.stage {
  max-width: 376px;
  margin: 0 auto;
}

.swiper-container {
  height: 240px;
}

.swiper-slide {
  border: 1px solid #ccc;
  transition: all .2s;
  height: 196px;
  width: 312px;
  transform: scale(0.9);
  background-color: white;
  border-radius: 10px;
  box-shadow: 0px 2px 8px 0px rgba(0, 0, 0, 0.25);
}

.swiper-slide-active {
  margin-top: 0;
  transform: scale(1);
}

.swiper-pagination-bullet-active {
  background-color: #006eb2;
}

.swiper-pagination-bullet {
  height: 12px !important;
  width: 12px !important;
}

@media only screen and (max-width: 376px) {
  .stage {
    width: 100vw;
  }
}
</style>
