<script setup>
import { ref } from 'vue'
const count = ref(0)
const increment = () => count.value++
const decrement = () => count.value--
</script>

<template>
<div class="counter">
  <h2>简易计数器</h2>
  <button @click="increment">+</button>
  <span>{{count}}</span>
  <button @click="decrement">-</button>
</div>
</template>

<style scoped>
.counter {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 30px;
}
</style>