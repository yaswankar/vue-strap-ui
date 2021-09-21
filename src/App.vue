<template>
  <div id="app">
    <vs-button width=200 height=50 color="#ffffff" bgColor="#000000" radius="5">sample</vs-button>
  </div>
</template>

<script>
import VsButton from './components/VsButton'
export default {
  name: 'App',
  components: {
    VsButton
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
