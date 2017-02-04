<template>
  <div id="app">
    <CompletedToDo></CompletedToDo>
    <GetToDo></GetToDo>
    <CurrentToDo></CurrentToDo>
  </div>
</template>

<script>

  import GetToDo from './components/GetToDo'
  import CurrentToDo from './components/CurrentToDo'
  import CompletedToDo from './components/CompletedToDo'

  export default {
    name: 'app',
    components: {
      GetToDo,
      CurrentToDo,
      CompletedToDo
    }
  }
</script>

<style>
  #app {
    font-family: Helvetica, sans-serif;
  }
</style>
