<template>
  <AppHeader msg="Welcome to Your Vue.js App" />
  <AppMonthChoice />
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import AppHeader from './components/AppHeader.vue'
import AppMonthChoice from './components/AppMonthChoice.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMonthChoice,
    HelloWorld,
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
  background-color: #DBE9F6;
}
</style>
