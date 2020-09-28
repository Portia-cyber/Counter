<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" class="logo">
    <design></design>
  </div>
</template>

<script>
import Design from './components/design.vue'

export default {
  name: 'App',
  components: {
    Design
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logo{
  display: block;
  margin: 0 auto;
  height: 70px;
}
</style>
