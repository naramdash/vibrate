<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import HelloWorld from './components/HelloWorld.vue'
import { useVibrate } from '@vueuse/core'

const { vibrate, stop, isSupported } = useVibrate({ pattern: [300, 100, 300] })

function startVibrate() {
  console.log("check")
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
  <div
    class="fullscreen"
    @mousedown.prevent="startVibrate()"
    @mousemove.prevent="startVibrate()"
    @mouseup.prevent="endVibrate()"
    @touchstart.prevent="startVibrate()"
    @touchmove.prevent="startVibrate()"
    @touchend.prevent="endVibrate()"
  >
    <h1 class="title">Click Me! Vibrate Me!</h1>
    <span>
      demonstrate
      <a href="https://vueuse.org/core/usevibrate/#usevibrate">vueuse3 useVibrate</a>
    </span>
    <img class="image" src="./assets/vibrator.png" />
  </div>
</template>

<style scoped>
.fullscreen {
  width: 100vw;
  height: 100vh;
}

.title {
  text-align: center;
}

.image {
  margin-left: 10vw;
  margin-right: 10vw;
  width: 80vw;
}
</style>
