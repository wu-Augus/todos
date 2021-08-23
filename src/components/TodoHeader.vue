<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" >
    <label for="toggle-all"></label>
    <input
    v-model.trim="mask"
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      @keyup.enter="onkeyup"
    />
  </header>
</template>


<script>
export default {
    props:['arr'],
    data(){
        return {
            mask:''
        }
    },

 methods:{
     onkeyup(){
// console.log(this.mask);
if(this.mask=='') return alert('请输入名称')
this.$emit('ceratTack',this.mask)//子项向父传数据
this.mask=''
     }
 }
}
</script>