<template>  
    <input 
      v-model="inputToDoTitle"
      type="text"
      class="form-control"
      placeholder="Please enter title"
      @keyup.enter="handleSubmit"> 
      <select id="priority">
      <option v-for="prio in props.prioArray" :key="prio" :value="prio.id" >{{prio.name}}</option>            
    </select>
        <textarea
      v-model="inputToDoDescription"
      placeholder="Please add description">
    </textarea><br>    
  <button @click="handleSubmit" class="btn btn-primary" type="button">add</button>
</template>

<script setup>
import { ref, defineEmits } from 'vue'
const inputToDoTitle = ref()
const inputToDoDescription = ref()
const props = defineProps(['index','prioArray'])

var new_index =props.index+1
console.log(props.prioArray)


const emits = defineEmits(['add'])
const handleSubmit = () => {
  emits('add', {id:new_index++, title:inputToDoTitle.value, description:inputToDoDescription.value, prio:priority.value,isCompleted:false})
  inputToDoTitle.value = ''
  inputToDoDescription.value = ''
  
}

</script>
