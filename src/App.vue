<template>
  <div id="app">
    <h1>TO-DO List</h1>
      <ToDoList/>
  </div>
</template>

<script>

import ToDoList from '../components/ToDoList.vue'
   

export default {
        name: 'app',
        components: {
            ToDoList
        }, 
    }
</script>

<style>
    #app {
        font-family: Calibri;
        font-weight:500;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #C8C8C8;
        align-items: center;
        margin-top: 30px;
        margin-right: 0px;
        margin-left: 0px;
        margin-bottom: 30px;
    }
    h1 {
        text-align:center;
    }

</style>
