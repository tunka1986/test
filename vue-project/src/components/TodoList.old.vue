<script>
  export default {
    data() {
      return {
        TodoList: [],
      };
    },
    methods: {
      addToDo(newitem) {
        this.TodoList.push(this.newitem);
      },
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
  <div id="app">
    <input v-model="newitem">
    <button @click="addToDo">Add</button>
    <button @click="Clear">Clear</button>
    <ul>
      <li v-for="(item, i) in TodoList" :key="i">{{ item }}<button @click="RemoveTodo(i)">X</button></li>
    </ul>
  </div>
  
</template>