<script setup>
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'

import { ref } from 'vue'
const ToDoItems = ref(null)

</script>

<template>
  <main>
    <TodoForm/>
    <TodoList />
    <ul class="parent list-group">
    <li class="list-group-item" v-for="i in ToDoItems?.list" :key="i">
      {{ i }}
    </li>
  </ul>
  </main>
</template>

