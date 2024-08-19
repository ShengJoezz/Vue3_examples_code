<template>
    <button @click="toggleList">Toggle List</button>
    <button @click="pushNumber">Push Number</button>
    <button @click="popNumber">Pop Number</button>
    <button @click="reverseList">Reverse List</button>
    <ul v-if="isShow && !isEmpty">
      <li v-for="n in List" :key="n">{{n}}</li>
    </ul>
    <p v-else-if="isEmpty">The List is empty!</p>
    <p v-else>You Hide The List!</p>
  </template>
  <script setup>
    import {ref,computed} from 'vue'
    const num=ref(1)
    const List=ref([num.value,++num.value,++num.value])
    const isShow = ref(true)
    const isEmpty = ref(false)
    //const isEmpty=computed(()=>List.value.length === 0)
    function toggleList(){
      isShow.value = !isShow.value
    }
    function pushNumber(){
      List.value.push(++num.value)
    }
    function popNumber(){
      if(num.value >0){
      List.value.pop()
      num.value--}
      else{
        num.value=0
        isEmpty.value=true
      }
    }
    //更好的写法应该是:const isEmpty=computed(()=>List.value.length === 0)
    function reverseList(){
      List.value.reverse()
    }
  </script>