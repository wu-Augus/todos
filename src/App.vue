<template>
  <div class="todoapp">
<todo-header @ceratTack='onCeratTsak'></todo-header>
<todo-main :arr="showArr" ></todo-main>
<todo-footer  :arr='list' @onclear='onclear' :active='isActive' @setActive='onsetActive'></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  watch:{
list:{
  deep:true,
handler(){
  localStorage.setItem('todoList',JSON.stringify(this.list))
}
}
  },
  data () {
    return {
   isActive:'all',// undone all done
list: JSON.parse(localStorage.getItem('todoList'))
    }
  },
components:{
TodoMain,
TodoHeader,
TodoFooter
},
  created () {

  },

  methods: {
onCeratTsak(taskName){
  const id=this.list[this.list.length-1].id+1
this.list.push({
  id,
  name:taskName,
  isDone:false
})
},
onclear(undone){
  this.list=undone
},
onsetActive(str){
  // console.log(str);
 return this.isActive=str 

}
  },
  computed:{
    showArr(){
      // console.log(123);
      if(this.isActive==='done'){
         return this.list.filter(obj => obj.isDone === true)
      }else if(this.isActive==='undone'){
         return this.list.filter(obj => obj.isDone === false)
      }else{
        return this.list

      }
    }
  }

}
</script>

<style scoped>

</style>
