<template>
  <div class="container">
<transition name="slide-down">
      <div class="title-wrapper" v-show="IfTitleAndMenuShow">
        <div class="left">
          <span class="icon-left"></span>
        </div>
        <div class="right">
            <div class="icon-wrapper">
              <span class="icon-bag"></span>
            </div>
            <div class="icon-wrapper">
              <span class="icon-person"></span>
            </div>
            <div class="icon-wrapper">
              <span class="icon-more"></span>
            </div>
        </div>
    </div>
    </transition>
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
.title-wrapper{
      position: absolute;
      top:0;
      left: 0;
      z-index: 101;
      width: 100%;
      height: px2rem(48);
      background: white;
      box-shadow: 0 px2rem(8) px2rem(8) rgba(0,0,0,.15);
    .left{
      flex: 0 0 px2rem(60);
      // width:49%;
      float: left;
      .icon-left{
        line-height: px2rem(48);
        font-size: px2rem(22);
      }
    }
    .right{
      float: right;
      width:49%;
      flex: 1;
      display: flex;
      justify-content: flex-end;
      .icon-wrapper{
        flex: 0 0 px2rem(60);
        height: 30rpx;
        width: 30rpx;
        @include center;
        .icon-bag{
            line-height: px2rem(48);
            font-size: px2rem(22)
        }
        .icon-person{
            line-height: px2rem(48);
            font-size: px2rem(22)
        }
        .icon-more{
            line-height: px2rem(48);
            font-size: px2rem(15);
        }
      }
    }
    // 这里移入global.scss
    // &.slide-down-enter, &.slide-down-leave-to {
    //   transform: translate3d(0,-100%,0)
    // }
    // &.slide-down-enter-to, &.slide-down-leave {
    //   transform: translate3d(0,0,0)
    // }
    // &.slide-down-enter-active, &.slide-down-leave-active {
    //   transition: all .5s linear;
    // }
  }
</style>
