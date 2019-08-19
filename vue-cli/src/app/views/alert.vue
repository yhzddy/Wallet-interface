 <template>
  <div class="dialog">
      <!--外层的遮罩 点击事件用来关闭弹窗，isShow控制弹窗显示 隐藏的props-->
      <div class="dialog-cover back"  v-if="isShow"></div>
      <transition name="fade">
         <!--style 通过props 控制内容的样式  -->
        <div class="dialog-content" :style="{top:topDistance+'%',width:widNum+'%',left:leftSite+'%'}"  v-if="isShow">
          <div class="dialog_main" :style="{paddingTop:pdt+'px',paddingBottom:pdb+'px'}">
            <!--弹窗的内容-->
            <slot class="main" name="main"></slot>
          </div>
        </div>
    </transition>
  </div>
</template>


<script>


export default {
  props: {
    isShow: {
    // 弹窗组件是否显示 默认不显示
      type: Boolean,
      default: false,
      required: true, // 必须
    },
    widNum: {
    // 内容宽度
      type: Number,
      default: 28,
    },
    leftSite: {
      // 左定位
      type: Number,
      default: 38,
    },
    topDistance: {
        // top上边距
      type: Number,
      default: 35,
    },
    pdt: {
      // 上padding
      type: Number,
      default: 18,
    },
    pdb: {
      // 下padding
      type: Number,
      default: 18,
    },
  },
  // methods: {
  //   closeMyself() {
  //     this.$emit('on-close')
  //     //
  //   },
  // },
}
</script>

<style socped>

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

  .dialog {
    position: relative;
    color: white;
    font-size: 32px;

  }

  .dialog-cover {
    background: rgba(0,0,0);
    position: fixed;
    z-index: 200;
    width: 200px;
    height: 200px;

  }
  .dialog-content{
    border-radius: 10px;
     background: rgba(0,0,0,0.8);
    position: fixed;
    top: 52%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 300;
 }

.main{
  width: 100%;
  height: 100%;
}
</style>

