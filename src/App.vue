<template>
  <div id="app">
    <toDoList></toDoList>
  </div>
</template>

<script>
import toDoList from './components/toDoList'

export default {
  name: 'app',
  components: {
    toDoList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
html {
    background-color: whitesmoke;
}
</style>
