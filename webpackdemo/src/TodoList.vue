<template>
<div id="app">
  <!-- 这里注意，由于模板里只能有一个元素，所以这里需要套一个div -->
  <div class="all">
    <input class="item" v-model="inputValue"/>

    <button  class="button"  @click="handlesubmit">提交</button>
  </div>

  <ul>
    <!-- 拆分组件 -->
  <todo-item 
v-for="(item,index) of list"
:key="index"
:content="item"
:index="index"
@deleteitem="handledelete"
  >
</todo-item>
  </ul>
    </div>
</template>

<script>
import TodoItem from './components/TodoItem'
export default {
 components:{
   'todo-item':TodoItem
 },

 data:function(){
   return {
     inputValue:'',
     list:[]
   }
 },

 methods:{
   handlesubmit(){
     this.list.push(this.inputValue),
     this.inputValue=""
   },
   handledelete:function(index){
     this.list.splice(index,1)
   }
 }
}
</script>

<style>
#app{
  height: 100%;
  width:100%;
}
.item{
  color:brown
}
.all{
  text-align: center;
  margin:0px auto;
  margin-top: 30rpx;
}
.button{
  display: block;
  margin: 0px auto;
}
</style>
