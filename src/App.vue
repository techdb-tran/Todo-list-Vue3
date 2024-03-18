<template>
    <div class="container">
    <h1>Todo-List</h1>
    <FormTodo/>
    </div>
</template>
<script setup>
import FormTodo from './components/form/FormTodo.vue';
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
h1 {
    font-size: 4rem;
    color: white;
    font-family: 'Poppins', sans-serif;
}
.container{
  text-align: center;
}
</style>