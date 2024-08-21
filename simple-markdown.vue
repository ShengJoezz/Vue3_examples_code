<template>
    <div class="editor">
     <textarea class="input" v-model="input" @input="update">
     </textarea>
    <div class="output" v-html='output'>
    </div>
    </div>
  </template>
  
  <script setup>
  import { marked } from 'marked'
  import { debounce } from 'lodash-es'
  import { ref, computed,onMounted } from 'vue'
  const input = ref('# Hello')
  const output = ref('')
  const update = debounce(()=>{output.value=marked(input.value)},100)
  onMounted(update)
  </script>
  
  <style scoped>
  body {
    margin: 0;
  }
  
  .editor {
    height: 100vh;
    display: flex;
  }
  
  .input,
  .output {
    overflow: auto;
    width: 50%;
    height: 100%;
    box-sizing: border-box;
    padding: 0 20px;
  }
  
  .input {
    border: none;
    border-right: 1px solid #ccc;
    resize: none;
    outline: none;
    background-color: #f6f6f6;
    font-size: 14px;
    font-family: 'Monaco', courier, monospace;
    padding: 20px;
  }
  
  code {
    color: #f66;
  }
  </style>