
<script>
import * from './TodoForm.vue'
  export default {
    methods: {
      RemoveTodo(index) {
        this.TodoList.splice(index,1);
      },
      Clear(){
        this.TodoList.splice(0);
      }
    }
  };
</script>
<template>
    <button @click="Clear">Clear</button>
    <ul>
      <li v-for="(item, i) in TodoList" :key="i">{{ item }}<button @click="RemoveTodo(i)">X</button></li>
    </ul>  

</template>
<form @submit.prevent="addToDo" ref="todo"></form>  
  