<template>
  <div id="app">
    <header class="app-header">
      <a href="https://whackathon.org/" target="_blank" class="logo container">
        <img id ="whackathon-logo" alt="Whackathon Logo" src="./assets/images/whackathon-logo.svg">
      </a>
    </header>

    <!-- Let's bring in the "Home" component
    and pass it the app title -->
    <Home :title="title"/>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'app',
  components: {
    Home
  },
  data () {
    return {
      title: 'Vue + Axios Template 🚀'
    }
  }
}
</script>

<style>
/* Make fonts render smoothly */
html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smothing: grayscale;
}

/* Reset Borders, Margins + Paddings */
* {
  border: 0;
  padding: 0;
  margin: 0;
}

body {
  font-family: "Nunito Sans", sans-serif;
  color: #5865FF;
  font-size: 17px;
}

.container {
  margin: 0 auto;
  max-width: 800px;
}
.logo {
  display: block;
}
.app-header {
  background: #5865FF;
  padding: 2.5rem 0;
}

</style>
