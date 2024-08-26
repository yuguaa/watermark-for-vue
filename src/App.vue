<template>
  <div id="app">
    <watermark :options="options">
      <div>123456</div>
    </watermark >
  </div>
</template>

<script>
import Watermark from 'watermark-for-vue'

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

</style>
