<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>
<script>
export default {
  name: 'App'
}
// eslint-disable-next-line
// 这里是为了屏幕自适应，使得字体可以自由缩放 
document.addEventListener('DOMContentLoaded', () => {
  const html = document.querySelector('html')
  let fontSize = window.innerWidth / 10
  fontSize = fontSize > 50 ? 50 : fontSize
  html.style.fontSize = fontSize + 'px'
})
</script>
<style>
#app{
  width: 100%;
  height: 100%;
}
</style>
