<template>
  <footer class="footer">
    <span class="todo-count">剩余<strong>数量值{{undone}}</strong></span>
    <ul class="filters" >
      <li>
        <a :class="{selected: active=='all'}" @click="$emit('setActive','all')" href="javascript:;" >全部</a>
      </li>
      <li>
        <a href="javascript:;" :class="{selected: active=='undone'}" @click="$emit('setActive','undone')">未完成</a>
      </li>
      <li>
        <a href="javascript:;" :class="{selected: active=='done'}" @click="$emit('setActive','done')" >已完成</a>
      </li>
    </ul>
    <button class="clear-completed" @click="onclear">清除已完成</button>
  </footer>
</template>


<script>
export default {
  data(){
    return {
       isSel: 'all'
    }
  },
  props:['arr','active','farr'],
 computed:{
   undone(){
   return this.arr.filter((item)=>{
       return item.isDone==false
     }).length
   }
 },
 methods:{
   //删除
   onclear(){
    const undone=this.arr.filter(item=>!item.isDone)
    this.$emit('onclear',undone)
   },
   
 }

}
</script>