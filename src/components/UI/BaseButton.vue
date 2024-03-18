<template><button>
    <slot></slot>
</button></template>
<style scoped>
button {
  width: 3rem;
  height: 3rem;
  background: white;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  border: none;
}
</style>