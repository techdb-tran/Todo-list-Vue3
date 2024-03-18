<template>
<div class="add-todo-container">
  <input type="text" v-model="inputTodo"/>
  <AddTodoButton @click="handleAdd"/>
</div>
</template>

<script setup>
import AddTodoButton from './AddTodoButton.vue';
import { ref } from 'vue';
const inputTodo = ref('');
const emit = defineEmits(['inputTodo']);
function handleAdd(){
  emit('inputTodo', inputTodo.value);
  inputTodo.value = '';
}

</script>

<style scoped>
.add-todo-container {
  display: flex;
  width: 30rem;
  height: 3rem;
}
input[type="text"]{
   width: 20rem;
   font-size: 2.5rem;
}
</style>