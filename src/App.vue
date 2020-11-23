<template>
  <div id="app">
    <vueHeader/>
    <vueSection/>
  </div>
</template>

<script>
import vueHeader from './components/vueHeader.vue'
import vueSection from './components/vueSection.vue'

export default {
  name: 'app',
  components: {
    vueHeader,
    vueSection,
  }
}
</script>

<style>
#app {
  margin: -8px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #cdcdcd;
  height: 100vh;
  width: 100vw; 
}
</style>
