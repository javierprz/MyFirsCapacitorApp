<template>
  <div id="app">
    <h1>Geolocation</h1>
    <div v-if="loc">
      <p>Your location is:</p>
      <p>Latitude: {{loc.coords.latitude}}</p>
      <p>Longitude: {{loc.coords.longitude}}</p>
    </div>

    <button @click="getCurrentPosition">
      Get Current Location
    </button>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core'
export default {
  name: 'App',
  data() {
    return{ loc: null }
  },
  methods: {
    async getCurrentPosition(){
      const { Geolocation } = Plugins;
      const loc = await Geolocation.getCurrentPosition()
      this.loc = loc
    }
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
