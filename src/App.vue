<template>
  <div class="container">
<!--    <Counter />-->
    <TodoList />
  </div>
</template>

<script setup>
import Counter from './components/Counter.vue'
import TodoList from './components/TodoList.vue'
</script>

<style scoped>
..container {
  width: 400px;
  margin: 50px auto;
  font-family: sans-serif;
}
</style>
