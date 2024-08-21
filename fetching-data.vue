<template>
    <h1>
      Latest Vue Core Commits
    </h1>
  <template v-for="branch in branches" :key="branch">
    <input type="radio" :id="branch" :value="branch" v-model="currentBranch">
    <label :for="branch">{{branch}}</label>
  </template>
    <p>vue@vuejs/{{currentBranch}}</p>
    <ul v-if="commits.length > 0">
      <li v-for="{ html_url, sha, author, commit} in commits" :key="sha">
       <a :href="html_url" target="_blank" class="commit">{{ sha.slice(0, 7) }}</a>
        -<span >{{commit.message}}</span>
        <br>
        by <a :href="author.html_url" class="author">{{commit.author.name}}</a>
        at <span class="time">{{formatDate(commit.author.date)}}</span>
      </li>
    </ul> 
  </template>
  
  <script setup>
    import {ref,watchEffect} from 'vue'
    const API_URL = 'https://api.github.com/repos/vuejs/core/commits?per_page=5&sha='
    const branches =['main','v2-compat']
    const currentBranch = ref(branches[0])
    const commits =ref([])
    watchEffect(async ()=>{
      const url = `${API_URL}${currentBranch.value}`
      commits.value = await(await fetch(url)).json()
    })
    function formatDate(v) {
    return v.replace(/T|Z/g, ' ')
  }
  </script>
  <style>
    a{
      color: #42b883;
    }
  li {
    line-height: 1.5em;
    margin-bottom: 20px;
  }
  .author,
    .time{
      font-weight: bold;
    }
  </style>