<template>
    <BaseButton>
        <p class="wrap-btn">+</p>
    </BaseButton>
</template>
<script setup>
import BaseButton from '../UI/BaseButton.vue'
</script>
<style scoped>
.wrap-btn {
    color: white;
    font-size: 2rem;
    background: #ff6f47;
    width: 2rem;
    height: 2rem;
    border-radius: 3px;
}
button:hover {
    background:#ff6f47;
}
button:hover .wrap-btn {
    background: white;
    color: #ff6f47;
}
</style>
