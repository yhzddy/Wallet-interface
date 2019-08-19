<template>
<div id="total">
  <div id="home">
    <div class="conimg">
      <img id="white" src="../../assets/images/Home_ETH1.png" alt="white" />
      <img id="black" src="../../assets/images/Home_ETH.png" alt="black" />
    </div>
    <p id="id2">{{text[1]}}</p>
    <button class="topbtn">{{text[2]}}</button>
    <p id="id3">{{text[3]}}</p>
    <div>
      <button class="bottombtn">{{text[4]}}</button>
      <button class="bottombtn">{{text[5]}}</button>
    </div>
    <img class="nextbtn" src="../../assets/images/nextbtn.png"/>
  </div>
  <vue-mid></vue-mid>
</div>
</template>

<script>
// import conImg from './container-img.vue'
import mid from '../views/container-mid'

export default {
  data() {
    return {
      text: [
        'BEPAL',
        'BEPAL Touch',
        '下载 BEPAL WALLET',
        '需搭配 BEPAL WALLET 使用',
        '使用说明',
        '常见问题',
      ],
    }
  },
  components: {
    'vue-mid': mid,
  },
}
</script>

<style lang="stylus" scoped>

@font-face {
    font-family: PingFangSC-Regular;
    src: url("../../assets/fonts/PingFang Regular.ttf");
}

@font-face {
    font-family: PingFangSC-Light;
    src: url("../../assets/fonts/PingFang Light.ttf");
}


#total{
  width :100%;
  overflow hidden;
}

.conimg {
  position: relative;
  height: 372px;
  width: 546px;
  margin-top: 376px;
}

#white {
  top: 0;
  left: 0;
  width: 100%;
  z-index: 0;
}

#black {
  position: absolute;
  top: 76px;
  left: 44px;
  width: 100%;
  z-index: 2;
}

#home {
  height: 1350px;
  background: url('../../assets/images/background.png') center no-repeat;
  background-size: 100% 100%;

  display: flex;
  display: -webkit-flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}

p#id2 {
  color: #262d33;
  font-family: PingFangSC-Regular, sans-serif;
  font-size: 32px;
  margin-top: 80px;
}

.topbtn {
  border: 2px solid #262d33;
  border-radius: 50px;
  width: 550px;
  background: #262d33;
  line-height :80px;
  font-family: PingFangSC-Regular, sans-serif;
  color: #fafafa;
  margin-top: 151px;
  font-size: 29px;
}

p#id3 {
  font-size: 28px;
  color: #ccd0d5;
  margin-top: 30px;
  margin-bottom: 40px;
  font-family: PingFangSC-Regular, sans-serif;
}

.bottombtn {
  border: 2px solid #9fa2a5;
  border-radius: 50px;
  width: 258px;
  background: #fafafa;
  line-height :72px;
  color :#3f4449;
  font-family: PingFangSC-Regular, sans-serif;
  font-size: 32px;
  margin: 0 17px;
}

.nextbtn{
  width :55px;
  height :25px;
  margin-top :30px;
  margin-bottom :32px;
}
</style>





