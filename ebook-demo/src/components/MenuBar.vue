<template>
  <div class="container">
<transition name="slide-up">
      <div class="menu-wrapper" v-show="IfTitleAndMenuShow">
        <div class="icon-wrapper">
          <span class="icon-other"></span>
        </div>
         <div class="icon-wrapper">
          <span class="icon-circle"></span>
        </div>
         <div class="icon-wrapper">
          <span class="icon-sunset"></span>
        </div>
         <div class="icon-wrapper">
          <span class="icon-a">A</span>
        </div>
    </div>
</transition>
    <div class="setting-wrapper">

    </div>
  
  </div>
</template>

<script>
export default {
  props: {
      IfTitleAndMenuShow: {
          type: Boolean,
          default: false
      }
  },
  data() {
    return {

    }
  },
  components: {

  }
}
</script>

<style scoped lang="scss">
@import '../assets/styles/globle';
.menu-wrapper{
     position: absolute;
      bottom:0;
      left: 0;
      z-index: 101;
      display: flex;
      width: 100%;
      height: px2rem(48);
      background: white;
      box-shadow: 0 px2rem(-8) px2rem(8) rgba(0,0,0,.15);
    .icon-wrapper{
      flex: 1;
      @include center;
      .icon-other{
       line-height: px2rem(48);
       font-size: px2rem(20)
      }
      .icon-circle{
        line-height: px2rem(48);
        font-size: px2rem(22)
      }
      .icon-sunset{
        line-height: px2rem(48);
        font-size: px2rem(25)
      }
      .icon-a{
        line-height: px2rem(48);
        font-size: px2rem(15)
      }
    }
    // 这里移入global.scss
    // &.slide-up-enter, &.slide-up-leave-to {
    //   transform: translate3d(0,100%,0)
    // }
    // &.slide-up-enter-to, &.slide-up-leave {
    //   transform: translate3d(0,0,0)
    // }
    // &.slide-up-enter-active, &.slide-up-leave-active {
    //   transition: all .3s linear;
    // }
  }
</style>
