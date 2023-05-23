<script setup>
import { ref } from 'vue'
import ToDoForm from './components/ToDoForm.vue'
const list = ref([])
// event handling function triggered by add
const AddToDo = value => {
  list.value.push(value)
}
const RemoveToDo = value => {
  list.value.splice(list.value.indexOf(value),1);
}
function ClearToDo() {
  list.value.splice(0);
}
</script>

<template>
  <div class="child-wrap input-group">
  <ToDoForm @add="AddToDo"></ToDoForm>
  <button @click="ClearToDo()">Clear</button>
  </div>
  <ul class="parent list-group">
    <li class="list-group-item" v-for="i in list" :key="i">{{ i }}<button class="remove_button" @click="RemoveToDo(i)">X</button></li>
  </ul>
 
</template>
