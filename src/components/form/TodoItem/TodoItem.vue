<template>
    <div class="todo-item-container">
      <span :class="{completed: completed}">{{ text }}</span>
      <BaseButton class="done-btn" @click="markAsDone">
        <svg fill="#FFFFFF" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24px" height="24px">
          <path
            d="M 19.980469 5.9902344 A 1.0001 1.0001 0 0 0 19.292969 6.2929688 L 9 16.585938 L 5.7070312 13.292969 A 1.0001 1.0001 0 1 0 4.2929688 14.707031 L 8.2929688 18.707031 A 1.0001 1.0001 0 0 0 9.7070312 18.707031 L 20.707031 7.7070312 A 1.0001 1.0001 0 0 0 19.980469 5.9902344 z" />
        </svg></BaseButton>
      <BaseButton class="delete-btn" @click="deleteTodo">
        <svg fill="#FFFFFF" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24px" height="24px">
          <path
            d="M 10 2 L 9 3 L 3 3 L 3 5 L 21 5 L 21 3 L 15 3 L 14 2 L 10 2 z M 4.3652344 7 L 5.8925781 20.263672 C 6.0245781 21.253672 6.877 22 7.875 22 L 16.123047 22 C 17.121047 22 17.974422 21.254859 18.107422 20.255859 L 19.634766 7 L 4.3652344 7 z" />
        </svg>
        </BaseButton>
    </div>
</template>
<script setup>
import BaseButton from "../../UI/BaseButton.vue";
const props = defineProps({
  id: {
    type: String,
    required: true
  },
  text: {
    type: String,
    required: true
  },
  completed: {
    type: Boolean,
    required: true
  }
});

const emit = defineEmits(['todo-updated', 'todo-deleted']);

function markAsDone() {
  if (props.id) {
    emit('todo-updated', props.id);
  } else {
    console.error('Invalid todo ID');
  }
}

function deleteTodo() {
  if (props.id) {
    emit('todo-deleted', props.id);
  } else {
    console.error('Invalid todo ID');
  }
}
</script>
<style src="./style.css" scoped>
</style>

