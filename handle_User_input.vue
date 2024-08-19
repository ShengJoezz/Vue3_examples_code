<template>
    <h1>{{msg}}</h1>
    <button @click="reverseMsg">Reverse The Msg</button>
    <button @click="append">append the !</button>
    <a href="https://vuejs.org" @click.prevent="notify">A link with e.PreventEvent()</a>
  </template>
  
  <script setup>
    import {ref} from 'vue'
    const msg =ref('Hello World!')
    const stringMsg=ref(null)
    function reverseMsg(){
      msg.value=msg.value.split('').reverse().join('')
    }
    function append(){
      stringMsg.value=msg.value.split('')
      stringMsg.value.push('!')
      msg.value=stringMsg.value.join('')
    }
      //这里应该用更简单的方式，因为msg是string,所以应该可以直接用msg.value += '!'，这里如果用数组的push方法，应该先把msg转化为数组，push方法只能返回修改后的数组长度，因此只能用一个中间变量存储，split和join是把原来的字符串划分和串联起来的方法
    function notify(){
      alert('navigation was prevented.')
    }
  
  </script>
  
  <style>
    button,a{
      display:block;
      margin-bottom: 1em;
    }
     /*这个 CSS 将按钮和链接设置为块级元素（display: block），并在它们之间添加了下边距，使它们垂直排列。
  </style>*/