<template>
  <div class="ebook">
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
    
    <div class="read-wrapper" @click="toggleTitleAndMenu">
        <div id="read"></div>
        <div class="mask">
          <div class="left" @click="prepage"></div>
          <div class="center" ></div>
          <div class="right" @click="nextpage"></div>
        </div>
    </div>
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
  </div>
</template>

<script>
import Epub from 'epubjs'
const DOWNLOAD_URL = '/static/Siddhartha.epub'
// 模块传入
// global.ePub = Epub
export default {
  mounted: function () {
    this.showEpub()
  },
  data () {
    return {
      IfTitleAndMenuShow: false
    }
  },
  methods: {
    // 电子书的解析和渲染
    showEpub () {
    // 生成Book对象
      console.log('here come')
      this.book = new Epub(DOWNLOAD_URL)
      console.log(this.book)
      // 生成Rendition,通过book对象的renderto
      this.rendition = this.book.renderTo('read', {
        width: window.innerWidth,
        height: window.innerHeight
      })
      // 通过Rendition.display渲染电子书
      this.rendition.display()
    },
    prepage () {
      // Rendition
      if (this.rendition) {
        this.rendition.prev()
      }
    },
    nextpage () {
      if (this.rendition) {
        this.rendition.next()
      }
    },
    toggleTitleAndMenu () {
      this.IfTitleAndMenuShow = !this.IfTitleAndMenuShow
    }
  }
}
</script>

<style scoped lang="scss">
@import 'assets/styles/global';
#read{
  text-align: center;
}
.ebook{
  position: relative;
  width: 100%;
  height: 100%;
  .read-wrapper{
    text-align: center;
     .mask{
       position: absolute;
       top: 0;
       left: 0;
       z-index: 100;
       width: 100%;
       height: 100%;
       display: flex;
       .left {
          flex: 0 0 px2rem(100);
       }
       .right{
         flex: 0 0 px2rem(100);
       }
       .center{
          flex: 1;
       }
  }
  }
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
  }
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
  }
}
</style>
