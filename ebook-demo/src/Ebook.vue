<template>
  <div class="ebook">
    <!--transition需要指定name,并包裹一个包含v-show 得div，vue会为transition包裹得div动态添加class-->
<title-bar :IfTitleAndMenuShow="IfTitleAndMenuShow"></title-bar>
    <div class="read-wrapper" >
        <div id="read"></div>
        <div class="mask">
          <div class="left" @click="prepage"></div>
          <div class="center" @click="toggleTitleAndMenu"></div>
          <div class="right" @click="nextpage"></div>
        </div>
    </div>
<menu-bar :IfTitleAndMenuShow="IfTitleAndMenuShow"></menu-bar>
  </div>
</template>

<script>
import TitleBar from '@/components/TitleBar'
import MenuBar from '@/components/MenuBar'
import Epub from 'epubjs'
const DOWNLOAD_URL = '/static/Siddhartha.epub'
// 模块传入
// global.ePub = Epub
export default {
  mounted: function () {
    this.showEpub()
  },
  components: {
    TitleBar,
    MenuBar
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
  
  
}
</style>
