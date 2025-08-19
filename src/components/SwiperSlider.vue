<template>
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <div class="swiper-slide"><img src="https://swiperjs.com/demos/images/nature-2.jpg"/>
      </div>
      <div class="swiper-slide"><img src="https://swiperjs.com/demos/images/nature-5.jpg"/>
      </div>
      <div class="swiper-slide"><img src="https://swiperjs.com/demos/images/nature-6.jpg"/>
      </div>
    </div>
    <!-- Add Pagination -->
    <div class="swiper-pagination"></div>
    <!-- Add Navigation -->
    <div class="swiper-button-next"></div>
    <div class="swiper-button-prev"></div>
  </div>
</template>

<script lang="ts">
import {defineComponent, onMounted} from 'vue';
import Swiper from 'swiper';
import {Navigation, Pagination, EffectCoverflow} from 'swiper/modules';
import 'swiper/swiper-bundle.css';

export default defineComponent({
  name: 'SwiperSlider',
  setup() {
    onMounted(() => {
      new Swiper('.swiper-container', {
        modules: [Navigation, Pagination, EffectCoverflow],
        loop: false,
        effect: 'coverflow',
        grabCursor: true,
        centeredSlides: true,
        slidesPerView: 'auto',
        speed: 700,
        coverflowEffect: {
          rotate: 50,
          stretch: 50,
          depth: 1,
          modifier: 1,
          slideShadows: true,
        },
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
      });
    });
  },
});
</script>

<style scoped>
.swiper-container {
  width: 100%;
  height: 400px;
  padding: 50px 0;
  position: relative;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #e5e5e5;
  height: 300px;
  margin: auto;
  overflow: hidden;
}

</style>
