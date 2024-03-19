<template>
<div class="add-todo-container">
  <input type="text" v-model.trim="inputTodo"/>
  <AddTodoButton @click="handleAdd"/>
</div>
</template>

<script setup>
import AddTodoButton from '../AddTodoButton/AddTodoButton.vue';
import { ref } from 'vue';
const inputTodo = ref('');
const emit = defineEmits(['inputTodo']);
function handleAdd(){
  emit('inputTodo', inputTodo.value);
  inputTodo.value = '';
}
</script>
<style src="./style.css" scoped>
</style>