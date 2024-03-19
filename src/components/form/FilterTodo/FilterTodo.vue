<template>
<select name="filter-todo" id="filter-todo" @change="handleChange($event.target.value)">
    <option value="all">All</option>
    <option value="completed">Completed</option>
    <option value="uncompleted">Uncompleted</option>
</select>
</template>
<script setup>
const emit = defineEmits(['filter']);
const handleChange = (item) => {
  emit('filter', item);
};
</script>
<style src="./style.css">
</style>