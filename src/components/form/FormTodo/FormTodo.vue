<template>
  <form class="form-container" @submit.prevent="handleSubmitForm">
    <AddTodo @inputTodo="updateTodo"/>
    <FilterTodo @filter="filterTodoList"/>
  </form>
  <TodoItem v-for="todo in filteredTodoList"
   :key="todo.id" :id="todo.id" :text="todo.text" :completed="todo.completed"
   @todo-updated="handleMakeDoneTodo" @todo-deleted="handleDeleteTodo"/>
</template>

<script setup>
import AddTodo from '../AddTodo/AddTodo.vue';
import FilterTodo from '../FilterTodo/FilterTodo.vue';
import TodoItem from '../TodoItem/TodoItem.vue';
import { ref, watch, onMounted } from 'vue';

const inputTodo = ref('');
const todoList = ref([]);
const filteredTodoList = ref([]);
const currentFilter = ref('all');

function handleSubmitForm() {
  if(inputTodo.value !==''){
    const newTodo = {
    id: new Date().toISOString(),
    text: inputTodo.value,
    completed: false,
  };
  todoList.value.unshift(newTodo);
  updateLocalStorage(todoList.value);
  filterTodoList();
  console.log(newTodo);
}

function updateTodo(todo) {
  inputTodo.value = todo;
  console.log(todo)
}

watch(inputTodo, (newValue) => {
  inputTodo.value = newValue;
});

function updateLocalStorage(newValue) {
  localStorage.setItem('k_l_t', JSON.stringify(newValue));
}

function filterTodoList(item='all') {
  currentFilter.value = item;
  if (item === 'all') {
    filteredTodoList.value = [...todoList.value];
  } else if (item === 'completed') {
    filteredTodoList.value = todoList.value.filter(todo => todo.completed);
  } else if (item === 'uncompleted') {
    filteredTodoList.value = todoList.value.filter(todo => !todo.completed);
  }
}

function handleMakeDoneTodo(todoId) {
  const todoIndex = todoList.value.findIndex(todo => todo.id === todoId);
  if (todoIndex !== -1) {
    todoList.value[todoIndex].completed = !todoList.value[todoIndex].completed;
    updateLocalStorage(todoList.value);
    if(currentFilter.value == 'all'){
      filterTodoList('all')
    }
    if(currentFilter.value == 'completed'){
      filterTodoList('completed')
    }
    if(currentFilter.value == 'uncompleted'){
      filterTodoList('uncompleted')
    }
  }
}

function handleDeleteTodo(todoId) {
  todoList.value = todoList.value.filter(todo => todo.id !== todoId);
  updateLocalStorage(todoList.value);
  filterTodoList();
}

onMounted(() => {
  const storedTodo = localStorage.getItem('k_l_t') || '[]';
  todoList.value = JSON.parse(storedTodo);
  filterTodoList();
});
</script>
<style src="./style.css">
</style>