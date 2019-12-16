<template>
  <div id="app">
    <h1>ToDo List</h1>
    <TaskList/>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'

export default {
  name: 'app',
  components: {
    TaskList
  }
}
</script>

<style>

body{
  background-color: #abc;
}

#app {
  width: 60%;
  max-width: 45rem;
  padding: 1em;
  margin: 1em auto;
  overflow: auto;
  background-color: white;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  
}
</style>
