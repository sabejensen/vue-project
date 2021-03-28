<template>
  <div id="app">
    <ExerciseList />
  </div>
</template>

<script>
import ExerciseList from './components/ExerciseList.vue'

export default {
  name: 'App',
  components: {
    ExerciseList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #4c49f5;
  margin-top: 60px;
}
</style>
