
<template>  
    <input 
      v-model="inputToDoTitle"
      type="text"
      class="form-control"
      placeholder="Please enter title"
      @keyup.enter="handleSubmit"> 
    <textarea
     v-model="inputToDoDescription"
    placeholder="Please add description">
  </textarea>
      <button @click="handleSubmit" class="btn btn-primary" type="button">add</button>
</template>
<script setup>
import { ref, defineEmits } from 'vue'
const inputToDoTitle = ref()
const inputToDoDescription = ref()
const entryId = ref(0)
const emits = defineEmits(['add'])
const handleSubmit = () => {
  emits('add', {id:entryId.value++, title:inputToDoTitle.value, description:inputToDoDescription.value, prio:1})
  inputToDoTitle.value = ''
  inputToDoDescription.value = ''
}
</script>
