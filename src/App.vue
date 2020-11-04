<template>
  <div id="app">
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
html, body {
  margin: 0;
  padding: 0;
  overflow: hidden;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  background: linear-gradient(45deg, tan 35%, royalblue);
  margin: 0;
  padding: 0;
  position: absolute;
  top: 0;
  overflow: scroll;
}
</style>
