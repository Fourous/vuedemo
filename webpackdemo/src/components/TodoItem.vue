<template>
 <li class="item" @click="handledelete">{{content}}</li>
</template>
<script>
// 声明父组件接收content属性
export default {
props:['content','index'],
methods:{
  handledelete:function(){
    // 这里用广播让父组件收到
    this.$emit('deleteitem',this.index)
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--这里得scope是只有在这个组件中，才生效，组件中最好是加入scope --> 

<style scoped>
.item{
  color: gray;
}
</style>
