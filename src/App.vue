<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <TextTranslate msg="Welcome to Your Vue.js App"/>
</template>

<script>
import TextTranslate from './components/TextTranslate.vue'

export default {
  name: 'App',
  components: {
    TextTranslate
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
