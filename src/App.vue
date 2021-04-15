<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <watermark >
      <template slot="content">
      <template>
         <slot name="content">55555555555555555555</slot>
    </watermark >
  </div>
</template>

<script>
import Watermark from './packages/watermark/Watermark.vue'

export default {
  name: 'App',
  components: {
    Watermark
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
