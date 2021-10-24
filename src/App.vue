<template>
  <div id="app">
    <!-- <vs-button class="btn-outline success" width=200 height=50 color="#316cad" radius="5">sample</vs-button> -->
    <Demo />
  </div>
</template>

<script>
import Demo from './components/Demo'
export default {
  name: 'App',
  components: {
    Demo
  }
}
</script>

<style>
@import './styles/variables.scss';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
