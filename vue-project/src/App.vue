<script setup>
import { ref } from 'vue'
import ToDoForm from './components/ToDoForm.vue'

//import ToDoFormModal from './components/ToDoFormModal.vue'
const list = ref([])
const prios= ref([
  { id: 0, name: "low", color: "background-color: cyan" },
  { id: 1, name: "normal", color: "background-color: orange" },
  { id: 2, name: "high", color: "background-color: red" }
])

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

function complete(status){
    return status !== 'active' ?  "text-decoration: line-through;" : "";
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
    <div v-if=!list.length>Nothing To Do</div>
    <li class="ToDoBox" v-for="entry in list" :key="entry">
      <div class="top_items">
        <div :style="complete(entry.status)" class="title">{{ entry.title }}</div>
        <div class="prio" :style='prios[entry.prio].color'>{{prios[entry.prio].name}}

<!--          <select>
            <option v-for="prio in prios" :key="prio" :value="prio.id" :selected="prio.id===entry.prio ? true : false ">{{prio.name}}</option>            
          </select>
        -->
             </div>
      </div>
      <div class="description">{{entry.description}}</div>
    </li>
  </ul>
</div>
</template>
