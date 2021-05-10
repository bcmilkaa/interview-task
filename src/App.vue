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
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #C8C8C8;
        margin-top: 30px;
        margin-right: 0px;
        margin-left: 0px;
    }

</style>
