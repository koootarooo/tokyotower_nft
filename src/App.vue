<template>
  <div id="app">
    <TokyoTower/>
  </div>
</template>

<script>
import TokyoTower  from './components/TokyoTower'

export default {
  name: 'App',
  components: {
    TokyoTower
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
