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
    }
  };
</script>

<template>
        <input v-model="newitem">
        <button @click="addToDo">Add</button>
</template>