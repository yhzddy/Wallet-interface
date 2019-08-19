<template>
  <div class="wrapper" ref="wrapper">
    <div>
      <video
        preload="false"
        poster="https://bepal.oss-cn-hangzhou.aliyuncs.com/H5Site/touch/video_post.jpg?ver0.2"
        controls
      >
        <source
          src="https://bepal.oss-cn-hangzhou.aliyuncs.com/H5Site/touch/touch_video.mp4"
          type="video/mp4"
        />您的浏览器不支持 video 标签。
      </video>
    </div>
    <div class="buycart">
      <p class="t1">{{title[0]}}</p>
      <p class="t2">{{title[1]}}</p>
      <p class="t3">{{title[2]}}</p>
      <button class="t4btn">{{title[3]}}</button>
    </div>
    <div class="swip">
      <p class="t4">{{title[4]}}</p>
      <p class="t5">{{title[5]}}</p>
      <!-- <slider ref="swp" @tap="actiontitle"></slider> -->
      <div class="banner">
        <ul>
          <li :class=" curindex ==index ? 'active' : 'dd'" v-for="(item,index) in title5" :key="index" @click="getIndex(index)">
            {{item}}
          </li>
        </ul>
      </div>
      <div class="carousel">
        <swiper class="container" :options="swiperOption" ref="photo">
          <swiper-slide class="card" v-for="(slide,index) in swiperSlides" :key="index">
            <div class="inner-card" :style="  {backgroundImage:'url('+slide+')'}"></div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
    <div class="func">
      <p class="t6">{{title2[0]}}</p>
      <p class="t7">{{title2[1]}}</p>
      <p class="t8">{{title2[2]}}</p>
      <p class="t9">{{title2[3]}}</p>
    </div>
    <div class="android_ios"></div>
    <div class="bottom">
      <ul class="ul_item">
        <li class="li_item">
          <span class="lastfont">{{title3[0]}}</span>
          <span class="lastcon1">Bepal01</span>
          <button class="lastbtn" data-clipboard-target=".lastcon1" @click = "createCopy()">复制</button>
        </li>
        <li class="li_item">
          <span class="lastfont">{{title3[1]}}</span>
          <span class="lastcon2">gyh543868082</span>
          <button class="lastbtn" data-clipboard-target=".lastcon2" @click = "createCopy">复制</button>
        </li>
        <li class="li_item">
          <span class="lastfont">{{title3[2]}}</span>
          <span class="lastcon3">business@bepal.pro</span>
          <button class="lastbtn" data-clipboard-target=".lastcon3" @click = "createCopy" >复制</button>
        </li>
        <alert :isShow="status.isShowPublish">
           <div class="dialog_publish_main" slot="main">
            复制成功
           </div>
        </alert>
      </ul>
    </div>
     <div class="contact">
      <p class="t11">{{title4[0]}}</p>
      <p class="t12">{{title4[1]}}</p>
      <p class="t12">{{title4[2]}}</p>
    </div>

  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import Clipboard from 'clipboard'
import alert from './alert'
import Bus from './Bus'


export default {


  data() {
    return {
      status: {
        isShowPublish: false,
        topNum: {
          type: Number,
          default: 35,

        },
      },
      curindex: 0,
      title: [
        'BEPAL Touch',
        '专为移动场景和入门用户设计',
        '数字资产冷存储设备',
        '官网购买',
        'Touch 定制',
        '全新的营销场景，强劲的品牌输出',
      ],
      title2: [
        'BEPAL Touch',
        '专为移动支付设计的卡片钱包',
        '支持Android/iOS   |   操作简单',
        '隐私安全   |   PIN码保护   |   支持跨链多币种',
      ],
      title3: ['客服微信', '商务微信', '商务合作'],
      title4: [
        '400-850-0585',
        '周一至周五 9:30-17:30',
        '2017-2018 BEPAL.PRO 版权所有ICP认证：浙ICP备17046487号',
      ],
      title5: ['贰周年', 'GXC', 'BTC', 'ETH'],
      swiperSlides: [
        '/src/assets/images/二周年.png',
        '/src/assets/images/right.png',
        '/src/assets/images/left.png',
        '/src/assets/images/GXC.png',
      ],
      swiperOption: {
        slidesPerView: 'auto',
        speed: 1000,

        centeredSlides: true,
      },
    }
  },
  computed: {
    swiper() {
      return this.$refs.photo.swiper
    },
  },
  methods: {

    getIndex(id) {
      this.curindex = id
      this.swiper.slideTo(id, 1000, false)
      console.log(this.swiper)
      console.log(id)
    },
    closeDialog() {

    },

    createCopy() {
      const clipboard = new Clipboard('.lastbtn')  // 此处为点击的dom的类名
      // eslint-disable-next-line no-unused-vars
      clipboard.on('success', e => {
        Bus.$emit('showpop', !this.status.isShowPublish)
        clipboard.destroy()
      })
      // eslint-disable-next-line no-unused-vars
      clipboard.on('error', e => {
        document.alert('复制失败')
        clipboard.destroy()
      })
    },
  },

  mounted() {
    const that = this
    const options = {
      click: true,
      taps: true,
    }
    that.scroll = new Bscroll(this.$refs.wrapper, options)
    Bus.$on('showpop', (data) => {
      that.status.isShowPublish = data
      setTimeout(() => {
        that.status.isShowPublish = false
      }, 2000)
    })
  },
  components: {
    // slider: swip,
    swiper,
    swiperSlide,
    alert,
  },
}
</script>


<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

@font-face {
  font-family: PingFangSC-Light;
  src: url("../../assets/fonts/PingFang Light.ttf");
}

@font-face {
  font-family: PingFangSC-Regular;
  src: url("../../assets/fonts/PingFang Regular.ttf");
}

.banner_item.active {
  color: #262d33;
  border: 1px solid #262d33;
}

.banner {
  padding-top: 50px;
  text-align: center;
  height: 120px;
}

.dd {
  display: inline-block;
  border: 2px solid #999;
  border-radius: 40px;
  margin-left: 6px;
  margin-right: 6px;
  font-size: 28px;
  line-height: 48px;
  padding: 0 30px;

  font-family: PingFangSC-Regular, sans-serif;
  color: #999;
}

li.active {
  display: inline-block;
  border-radius: 40px;
  margin-left: 6px;
  margin-right: 6px;
  font-size: 28px;
  line-height: 48px;
  padding: 0 30px;
  font-family: PingFangSC-Regular, sans-serif;
  color: #262d33;
  border: 2px solid #262d33;
}

.carousel {
  width: 100%;
}
.swiper-container {
  overflow: hidden;
}
.card {
  width: 551px;
  margin: 0px 15px 30px 10px;
}

.inner-card {
  border-radius: 10px 10px 0 0;
  width: 551px;
  height: 293px;
  background-position: center;
  background-size: cover;
}

.wrapper {
  width: 100%;
}

p.t1 {
  font-size: 70px;
  margin-top: 105px;
  font-family: PingFangSC-Light, sans-serif;
  color: #bbbbbb;
}
p.t2 {
  font-size: 32px;
  margin-top: 8px;
  font-family: PingFangSC-Light, sans-serif;
  color: #bbbbbb;
}
p.t3 {
  font-size: 20px;
  margin-top: 20px;
  /* width: 220px; */
  padding: 0 20px;
  text-align: center;
  border: 2px solid #bbbbbb;
  line-height: 37px;
  border-radius: 50px;
  font-family: PingFangSC-Light, sans-serif;
  color: #bbbbbb;
}
p.t4 {
  font-family: PingFangSC-Light, sans-serif;

  font-size: 70px;
  color: #262d33;
  margin-top: 124px;
}
p.t5 {
  font-family: PingFangSC-Light, sans-serif;
  color: #5c5f62;
  font-size: 32px;
  margin-top: 35px;
}

p.t6 {
  margin-top: 100px;
  font-family: PingFangSC-Light, sans-serif;
  font-size: 70px;
  color: #dedfdf;
}
p.t7 {
  margin-top: 15px;
  white-space: pre;
  font-family: PingFangSC-Light, sans-serif;
  font-size: 32px;
  color: #dedfdf;
}
p.t8 {
  white-space: pre;
  margin-top: 35px;
  font-family: PingFangSC-Light, sans-serif;
  font-size: 20px;
  color: #a8a8a9;
}
p.t9 {
  white-space: pre;
  margin-top: 16px;
  font-family: PingFangSC-Light, sans-serif;
  font-size: 20px;
  color: #a8a8a9;
}
p.t10 {
  font-family: PingFangSC-Regular, sans-serif;
  font-size: 28px;
  color: #666666;
  padding: 30px 0px 30px 30px;
}
p.t11 {
  font-family: PingFangSC-Regular, sans-serif;
  font-size: 36px;
  padding: 30px 0px 5px 30px;
  color: #262d33;
}
p.t12 {
  font-family: PingFangSC-Regular, sans-serif;
  font-size: 22px;
  padding: 0px 0px 30px 30px;
  color: #666666;
}

.line {
  border: 1px solid #eeeeee;
}
.bottombtn {
  background-color: #ffffff;
  border: 1px solid #eeeeee;
  padding-right: 30px;
}
.t4btn {
  border-radius: 50px;
  border: 0 solid #e4ca97;
  width: 550px;
  text-align: center;
  line-height: 82px;
  font-family: PingFangSC-light, sans-serif;
  font-size: 32px;
  background: #e4ca97;
  margin-top: 440px;
  margin-bottom: 30px;
  color: #262d33;
}

video {
  height: auto;
  width: 100%;
  vertical-align: middle;
}

.buycart {
  height: 892px;
  background: url("../../assets/images/buycart.png") center no-repeat;
  background-size: 100% 100%;
  display: flex;
  display: -webkit-flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}
.swip {
  height: 900px;
  background: url("../../assets/images/gray.png") center no-repeat;
  background-size: 100% 100%;
  display: flex;
  display: -webkit-flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}

slider {
  overflow: hidden;
}

.func {
  height: 1700px;
  background: url("../../assets/images/func.png") center no-repeat;
  background-size: 100% 100%;
  display: flex;
  display: -webkit-flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}

.android_ios {
  height: 1800px;
  background: url("../../assets/images/AndiOS.png") center no-repeat;
  background-size: 100% 100%;
  display: flex;
  display: -webkit-flex;
  width: 100%;
}

.bottom {
  height: auto;
  background: #fafafa;
  background-size: 100% 100%;
  display: flex;
  align-items: center;
  justify-content:center;
  width: 100%;
}


.ul_item {
  margin:80px 22px 0 22px;
  height: 280px;
  width: 100%;
  display: flex;
  box-shadow: 6px 10px  20px rgba(0,0,0,.06);
  border-radius: 50px;
  background-color: #fff;
  flex-direction: column;
  border: 2px solid rgb(58, 59, 59,.08);
  border-radius: 10px;


}

.li_item {
  height: 300px;
  background-color: #fff;
    display: flex;
    align-items: center;
    padding: 0 20px;
    border-radius: 10px;
      /* border-bottom: 1px solid #eee; */
    border-bottom: 2px solid rgb(58, 59, 59,.08);
}

.lastfont{
  font-size: 28px;
      color: #262D33;
      font-family:  PingFangSC-Regular, sans-serif;
}

.lastcon1,.lastcon2,.lastcon3{
      flex: 1;
    text-align: right;
    padding-right: 30px;
    color: #666666;
}

.lastbtn{
  padding: 2px 12px;
  border: 2px solid #ddd;
  background-color: #ffffff;
  border-radius: 3px;
  color: #262d33;
  font-family:  PingFangSC-Regular, sans-serif;
  font-size: 24px;
}

.contact{

  width: 100%;
}


</style>

