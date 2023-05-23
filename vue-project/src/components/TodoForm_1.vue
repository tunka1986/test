<script setup>
    import { ref, defineExpose } from 'vue'
    const ToDoList = ref([])
    const value = ref('')
    const addToDo = () => {
        ToDoList.value.push(value.value)
        value.value = ''
    }
    defineExpose({ ToDoList })
</script>

<template>
        <input v-model="value" type="text" placeholder="Please enter">
        <button @click="addToDo">Add</button>
</template>
