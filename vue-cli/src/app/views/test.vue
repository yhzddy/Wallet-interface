
  <template>
  <div class="slider" ref="slider">
    <swiper class="container" :options="swiperOption">
      <swiper-slide class="card" v-for="slide in swiperSlides" :key="slide.id">
        <img :src="slide" />
      </swiper-slide>
      <!-- <swiper-slide><img src="/src/assets/images/二周年.png" ></swiper-slide>
      <swiper-slide><img src="/src/assets/images/left.png" ></swiper-slide>
      <swiper-slide><img src="/src/assets/images/right.png"></swiper-slide>-->
    </swiper>
    <!--以下看需要添加-->
    <!-- <div class="swiper-scrollbar"></div> //滚动条
    <div class="swiper-button-next"></div> //下一项
    <div class="swiper-button-prev"></div> //上一项
    <div class="swiper-pagination"></div> //标页码-->
  </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  data() {
    return {
      title: ['贰周年', 'GXC', 'BTC', 'ETH'],
      swiperSlides: [
        '/src/assets/images/二周年.png',
        '/src/assets/images/left.png',
        '/src/assets/images/right.png',
      ],
      swiperOption: {
        // autoplay: {
        //   delay: 3000,
        //   disableOnInteraction: false,
        // },
        slidesPerView: 'auto',
        speed: 1000,
        loop: false,
        // centeredSlides: true,
        // spaceBetween: 20,
        // loopAdditionalSlides: 100,
        // coverflowEffect: {
        //   rotate: 0,
        //   stretch: 120,
        //   depth: 100,
        //   modifier: 1,
        //   slideShadows: true,
        // },
      },
    }
  },
  components: {
    swiper,
    swiperSlide,
  },
}
</script>

<style scoped>
.slider{
  overflow: visible;
}
.container {
  width: 100%;
  margin: 0 30px;
}
/* swiper-slide {
  width: 551px;
  height: 293px;
  margin: 0 30px;
} */

img {
  width: 551px;
  height: 293px;
}
</style>
