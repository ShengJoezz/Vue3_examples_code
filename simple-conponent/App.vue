<template>
    <ol>
    <TodoItem v-for="item in todo" :key="item.id" :todo="item"/>
    </ol>
  </template>
  <script setup>
    import TodoItem from './TodoItem.vue'
    import {ref} from 'vue'
    const todo = ref([
      {id : 0,text : 'react'},
      {id : 1,text : 'vue'},
      {id : 2,text : 'js'}
    ])
  </script>