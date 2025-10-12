<script setup>
import { ref } from 'vue'

import TodosAPI from '@/apis/components/todos/TodosAPI.js';

defineProps({
  msg: String,
})

const count = ref(0)
const lstTodo = ref([])
TodosAPI.getAll().then(res => {
  lstTodo.value = res.data;
  console.log('lstTodo', res.data);
})
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
  </div>

  <ul>
    <li v-for="todo in lstTodo" :key="todo.id">
      {{ todo.title }}
    </li>
  </ul>
</template>