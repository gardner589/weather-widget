<template>
  <div id="app">
    <img src="./assets/logo.png">
    <Container/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Container from './components/Container'

export default {
  name: 'App',
  components: {
    Container
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
