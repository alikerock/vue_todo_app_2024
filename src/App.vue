<script setup>
import { RouterLink, RouterView } from 'vue-router'
import TodoItem from './components/TodoItem.vue';

</script>

<template>
 <div id="app" class="container">
  <h1>Vue Todo App</h1>
  <BFormInput placeholder="할일을 입력하세요" />
  <TodoItem todo="맛난거 먹기"/>

 </div>
</template>

<style scoped>
</style>
