<template>
  <div id="app">
    <img id ="whackathon-logo" alt="Whackathon Logo" src="./assets/whackathon-logo.svg">
    <Home msg="Vue.js and axios template"/>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'app',
  components: {
    Home
  }
}
</script>

<style>
#app {
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

#whackathon-logo {
  width: 30em;
}

body {
  background-color: #4B8CFF;
}
</style>
