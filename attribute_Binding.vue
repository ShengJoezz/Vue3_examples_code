<template>
    <p :title="msg">Hover your mouse over me for a few seconds to see my dynamically bound title!</p>
    <p :class="{red : isRed}" @click='toggleRed'>This should be red... but click me to toggle it.</p>
    <p :style="{color : isGreen?'green':'blue'}" @click="toggleGreenBlue">This should be green, and should toggle between green and blue on click.</p>
  </template>
  <script setup>
    import {ref} from 'vue'
    const msg=ref('Hello!')
    const isRed=ref(true)
    const isGreen=ref(true)
    function toggleRed(){
      isRed.value = !isRed.value
    }
    function toggleGreenBlue(){
      isGreen.value = !isGreen.value
    }
  </script>
  <style>
    .red{
      color:red;
    }
  </style>