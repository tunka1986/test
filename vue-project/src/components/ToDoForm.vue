<template>
    <input 
      v-model="value"
      type="text"
      class="form-control"
      placeholder="Please enter"
      @keyup.enter="handleSubmit"
      ref="text_input"
      >
      <button @click="handleSubmit" class="btn btn-primary" type="button">add</button>

</template>
<script setup>
import { ref, defineEmits } from 'vue'
const value = ref('')
const emits = defineEmits(['add'])
const handleSubmit = () => {
  emits('add', value.value)
  value.value = ''
}
import { nextTick } from 'vue';
</script>