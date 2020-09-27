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

    <h1>Device Info</h1>
    <div v-if="deviceInfo">
      <p>OS: {{deviceInfo.platform}} {{deviceInfo.osVersion}}</p>
      <p>Model: {{deviceInfo.model}}</p>
      <p>Manufacturer: {{deviceInfo.manufacturer}}</p>
      <p>UUID: {{deviceInfo.uuid}}</p>
    </div>
    <button @click="getDeviceInfo">
      Get Device Info
    </button>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core'
export default {
  name: 'App',
  data() {
    return{
      loc: null,
      deviceInfo: null
    }
  },
  methods: {
    async getCurrentPosition () {
      const { Geolocation } = Plugins;
      this.loc = await Geolocation.getCurrentPosition()
    },
    async getDeviceInfo () {
      const { Device } = Plugins
      this.deviceInfo = await Device.getInfo()
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
