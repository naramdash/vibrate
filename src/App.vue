<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import HelloWorld from './components/HelloWorld.vue'
import { useVibrate } from '@vueuse/core'

const { vibrate, stop, isSupported } = useVibrate({ pattern: [300, 100, 300] })

function startVibrate() {
  if (isSupported)
    vibrate()
  else
    alert("vibrate not supported")
}

function endVibrate() {
  stop()
}

</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <h1
    @mousedown="startVibrate()"
    @mousemove="startVibrate()"
    @mouseup="endVibrate()"
    @touchstart="startVibrate()"
    @touchmove="startVibrate()"
    @touchend="endVibrate()"
  >Vibe Me</h1>
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
</template>

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
