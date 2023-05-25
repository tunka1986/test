<script setup>
import { ref } from 'vue'
import ToDoForm from './components/ToDoForm.vue'
//import ToDoFormModal from './components/ToDoFormModal.vue'
const list = ref([])
const prios=[
  { id: 0, name: "low", color: "cyan" },
  { id: 1, name: "normal", color: "yellow" },
  { id: 2, name: "high", color: "red" }
]
const AddToDo = inputToDo => {
  list.value.push(inputToDo)
}
const RemoveToDo = value => {
  list.value.splice(list.value.indexOf(value),1);
}
function ClearToDo() {
  list.value.splice(0);
}
const open = ref(false)
function modalState(){
  return open.value ===true ? "opacity:30%; pointer-events:none; " : "";
}

</script>


<template>
<div v-if="open" class="modal">
  <div class="child-wrap input-group">
    <ToDoForm @add="AddToDo"></ToDoForm>
    <button @click="ClearToDo">Clear</button>
  </div>
  <button @click="open = false">Close</button>
</div>

<div class="modal-overlay" :style="modalState()">
<div class="header">
<div>To do list</div>
<div><img src = "./assets/icon_add.svg" alt="Add To DO Item" @click="open = true" >
  </div>
</div>

  <ul class="parent list-group">
    <li class="ToDoBox" v-for="entry in list" :key="entry">
      <div class="top_items">
        <div class="title">{{ entry.title }}</div>
        <div class="prio">
          <select>
            <option v-for="prio in prios" :key="prio" :value="prio.id" :selected="prio.id===entry.prio ? true : false ">{{prio.name}}</option>
            
          </select>
        </div>
      </div>
      <div class="description">{{entry.description}}</div>
    </li>
  </ul>
</div>
</template>
