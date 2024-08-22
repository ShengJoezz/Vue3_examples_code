<template>
    <h2>List Vuejs Branches</h2>
    <template v-for="branch in branches" :key="branch">
      <input type="radio" v-model="currentBranch" :value="branch" :id="branch">
      <label :for="branch">{{branch}}</label>
    </template>
    <br>
    <p>@vuejs/core/{{currentBranch}}</p>
    <ul >
      <li v-for="commit in commits" :key="commit.sha">
        <a :href="commit.html_url">{{commit.sha.slice(0,5)}}</a>
       - <span>{{commit.commit.message}}</span>
        <br>
        <a :href="commit.author.html_url">{{commit.commit.author.name}}</a>
         at <span class="date"> {{real_time(commit.commit.author.date)}} </span>
      </li>
    </ul>
  </template>
  <script setup>
    import {ref,watchEffect} from 'vue'
    const API_URL ='https://api.github.com/repos/vuejs/core/commits?per_page=5&sha='
    const branches=ref(['main','minor'])
    const currentBranch = ref(branches.value[0])
    const getdata_URL=`${API_URL}${currentBranch.value}`
    const commits = ref([])
    watchEffect(async()=>{
      commits.value = await (await fetch(getdata_URL)).json()
    })
    function real_time(t){
      return t=t.replace(/[TZ]/g," ")
    }
  </script>
  <style>
    a{
     text-decoration : none;
     color: #006400;
    }
    li {
    line-height: 1.5em;
    margin-bottom: 20px;
  }
    .date{
      font-weight : bold;
    }
  </style>