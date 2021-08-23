<template>
  <ul class="todo-list">
    <!-- completed: 完成的类名 -->
    <li :class="{completed:item.isDone}" v-for="(item,index) in arr" :key="item.id">
      <div class="view">
        <input class="toggle" type="checkbox" v-model="item.isDone" />
        <label>{{item.name}}</label>
        <button class="destroy" @click="onDel(index)"></button>
      </div>
    </li>
  </ul>
  
</template>


<script>
export default {
    props:['arr','farr'],//复杂数据类型 值可改变
    methods:{
      onDel(i){
       this.arr.splice(i,1)
      }
    }
}
</script>