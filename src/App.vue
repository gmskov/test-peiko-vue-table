<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/peiko-logo-mini.png">
    <h1>Test</h1>
    <hr>
    <InformationBar />
  </div>
</template>

<script>
import InformationBar from "@/components/InformationBar"

export default {
  name: 'App',
  components: {
    InformationBar
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
