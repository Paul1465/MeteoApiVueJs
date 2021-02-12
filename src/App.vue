<template>
  <div id="app">
    <meteo-api></meteo-api>
  </div>
</template>

<script>
import MeteoApi from './components/MeteoApi.vue'

export default {
  name: 'App',
  components: {
    'meteoApi' : MeteoApi
  }
}
</script>

<style>
body {
  background: #43c6ac;
  background: linear-gradient(to right, #f8ffae, #43c6ac);
}
</style>
