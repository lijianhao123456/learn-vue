<template>
  <div id="app">
    <vheader/>
    <vsection/>
  </div>
</template>

<script>
import vheader from './components/vheader.vue'
import vsection from './components/vsection.vue'

export default {
  name: 'app',
  components: {
    vheader,
    vsection,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #cdcdcd;
  height: 100vh;
  width: 100vw; 
}
</style>
