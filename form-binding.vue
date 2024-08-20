<template>
    <h2>Text here</h2>
    <input type='text' v-model="text">
    <p>{{text}}</p>
    
    <h2>Checkbox</h2>
    <input type='checkbox' id='checkbox' v-model='checkbox'>
    <label for='checkbox'>checkbox:{{checkbox}}</label>
    
    <h2>Multibox</h2>
    <input type='checkbox' id='jack' value='jack' v-model='multiBox'>
    <label for='jack'>jack</label>
    <input type='checkbox' id='mike' value='mike' v-model='multiBox'>
    <label for='mike'>mike</label>
    <input type='checkbox' id='mary' value='mary' v-model='multiBox'>
    <label for='mary'>mary</label>
    <p>checked names={{multiBox}}</p>
    <!-- <p v-for="t in multiBox" :key="t">{{t}}</p> -->
    
    <h2>Radio</h2>
    <input type='radio' id='one' value='one' v-model='checked'>
    <label for='one'>one</label>
    <br>
    <input type='radio' id='two' value='two' v-model='checked'>
    <label for='two'>two</label>
    <p>picked:{{checked}}</p>
    
    <h2>selected</h2>
    <select v-model='select'>
    <option disabled>please select one</option>
    <option>A</option>
    <option>B</option>
    </select>
    <p>you select {{select}}</p>
    
    <h2>multiSelect</h2>
    <select v-model='multiSelect' multiple >
      <option disabled>please select</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <p>you select {{multiSelect}}</p>
  </template>
  <script setup>
    import {ref} from 'vue'
    const text = ref('Edit me')
    const checkbox = ref(false)
    const multiBox=ref([])
    const checked=ref('one')
    const select=ref('')
    const multiSelect=ref([])
  </script>