<template>
  <div id="app">
    <watermark :options="options">
      <template slot="content">
        <div class="container">
          内容区域
        </div>
      </template>
    </watermark >
  </div>
</template>

<script>
import Watermark from './packages/watermark/Watermark.vue'

export default {
  name: 'App',
  components: {
    Watermark
  },
  data() {
    return {
      options:{
        content:123,
        src:require('@/assets/logo.png')
      }
    }
  },
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
.container{
  position: relative;
  height: 200px;
  border: 1px solid red;
  z-index: 200000000000000;
}
</style>
