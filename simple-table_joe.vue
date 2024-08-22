<template>
    <table>
    <thead>
      <th v-for="column in columns" :key="column">{{column}}</th>
    </thead>
    <tbody>
  <!-- 一个表格(table)需要thead,th(table header)来组成第一行的表头，tr(table row),td(table data)来组成每一行的内容--> 
      <tr v-for="data in datas" :key="data">
        <td v-for="column in columns" :key="column">
  <!--这种循环你只用观察是什么作为循环就可以了 -->
          {{data[column]}}
        </td>
      </tr>
    </tbody>
    </table>
  </template>
  <script setup>
    import {ref} from 'vue'
    const columns = ref(['Name','Time','Content'])
    const datas = ref([
      {Name:'Liu',Time:'Primary School',Content:'Strong'},
      {Name:'Wang',Time:'Senior High School',Content:'Little'},
      {Name:'Guo',Time:'University',Content:'Strong'}
    ])
  </script>
  <style scoped>
  table {
    border-collapse: collapse;
    width: 100%;
  }
  th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
  }
  th {
    background-color: #f2f2f2;
  }
  </style>