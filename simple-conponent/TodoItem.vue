<template>
    <li>{{todo.text}}</li>
  </template>
  <script setup>
    defineProps({
      todo :{
        id:Number,
        text:String
      }
    })
  </script>