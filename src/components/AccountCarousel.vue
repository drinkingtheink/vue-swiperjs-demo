<template>
  <div class="account-carousel-stage">
    <swiper 
      class="account-carousel"
      ref="accountCarousel" 
      :options="carouselOptions"
    >
      <swiper-slide 
        v-for="account in accounts"
        :key="account.name"
      >{{ account.name }}</swiper-slide>
      
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
        spaceBetween: 10, // achieves the 15px gap between carousel slides as prescribed in final design
        grabCursor: true,
        // slidesPerView: 'auto', // this combined with set width of carousel panes gives us the "peeking" effect
        slidesPerView: 1.2,
        centeredSlides: true,
        centerInsufficientSlides: true,
        a11y: {
          containerMessage: 'Your Accounts',
          paginationBulletMessage: 'Go to Account {{index}}',
          lastSlideMessage: 'This is the last Account in this list'
        }
      },
      activePaneIndex: 0,
      accounts: [
        {
          name: 'Account 1'
        },
        {
          name: 'Account 2'
        },
        {
          name: 'Account 3'
        },
        {
          name: 'Account 4'
        },
        {
          name: 'Account 5'
        },
      ]
    }
  },
  components: {
    Swiper,
    SwiperSlide
  },
  computed: {
    swiperInstance() {
      return this.$refs.accountCarousel.$swiper;
    }
  },
  methods: {
    goToPane(paneIndex) {
      this.swiperInstance.slideTo(paneIndex);
      this.updateActivePaneIndex(paneIndex);
    },
    updateActivePaneIndex(paneIndex) {
      this.activePaneIndex = paneIndex;
    }
  },
  mounted() {
    console.log('Current Swiper instance object', this.swiperInstance)
  },
  beforeDestroy() {
    this.swiperInstance.destroy();
  }
}
</script>

<style>
/** SWIPER STYLES **/

.account-carousel-stage {
  max-width: 430px;
  margin: 0 auto;
}

.swiper-container {
  height: 240px;
}

.swiper-slide {
  border: 1px solid #ccc;
  transition: all .2s;
  height: 166px;
  width: 312px;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0px 2px 8px 0px rgba(0, 0, 0, 0.25);
  margin-top: 10px;
}

.swiper-slide-active {
  margin-top: 0;
  transform: scale(1);
  height: 196px;
  margin-top: 0;
}

/** PAGINATION */ 
.swiper-pagination-bullet {
  height: 12px;
  width: 12px;
  opacity: 0.7;
  margin: 0 0.5rem 0 0;
  transition: all 0.2s;
  background-color: #ccc;
}

.swiper-pagination-bullet-active {
  background-color: #006eb2;
  opacity: 1;
}

.swiper-pagination-bullet-active:hover {
  opacity: 1;
}

/** MEDIA QUERIES */
@media only screen and (max-width: 376px) {
  .stage {
    width: 100vw;
  }
}
</style>
