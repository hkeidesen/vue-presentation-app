<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>

import Home from './components/Home'

export default {
  name: 'App',
  components: {
    Home
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0f204b;
  margin-top: 60px;
}
</style>
