<template>
    <swiper
      @slideChange="onSlideChange"
      class="swiper"
      :loop="true"
      :navigation="true"
      :modules="[Autoplay, Navigation, Pagination, EffectFade]"
      :pagination="{ clickable: true, hideOnClick: true }"
      :slides-per-view="1"
      :autoplay="{ delay: 3000, disableOnInteraction: false }"
      effect="fade"
    >
      <swiper-slide>
        <img src="~/assets/images/starSign1.png" class="h-50 w-50" alt="starSign1 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign2.png" class="h-50 w-50" alt="starSign2 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign3.png" class="h-50 w-50" alt="starSign3 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign4.png" class="h-50 w-50" alt="starSign4 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign5.png" class="h-50 w-50" alt="starSign5 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign6.png" class="h-50 w-50" alt="starSign6 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign7.png" class="h-50 w-50" alt="starSign7 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign8.png" class="h-50 w-50" alt="starSign8 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign9.png" class="h-50 w-50" alt="starSign9 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign10.png" class="h-50 w-50" alt="starSign10 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign11.png" class="h-50 w-50" alt="starSign11 pic">
      </swiper-slide>
      <swiper-slide>
        <img src="~/assets/images/starSign12.png" class="h-50 w-50" alt="starSign12 pic">
      </swiper-slide>
    </swiper>
  </template>
  
  <script setup>
  import '~/assets/css/tailwind base.css';
  import { Swiper, SwiperSlide } from 'swiper/vue';
  import { Autoplay, Navigation, Pagination, EffectFade } from 'swiper/modules';
  
  import 'swiper/css';
  import 'swiper/css/navigation';
  import 'swiper/css/pagination';
  import 'swiper/css/autoplay';
  import 'swiper/css/effect-fade';
  
  const onSlideChange = () => {
    console.log('slide changed');
  };
  </script>

  <style>
    
</style>