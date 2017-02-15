<template>
  <div id="app">
    <navigation></navigation>
  </div>
</template>

<script>
// Application dependencies
import Navigation from './components/Navigation'
import Vue from 'vue'
import VueSocketio from 'vue-socket.io'

// Sets up the websockets connection
Vue.use(VueSocketio, 'http://localhost:4001');

export default {
  name: 'app',
  components: {
    Navigation
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
}

html, body{
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}
</style>
