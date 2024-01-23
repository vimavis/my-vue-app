<script setup>
import { computed } from 'vue'

const props = defineProps({
  index: Number,
  name: String,
  timeMs: Number,
  active: Boolean
})

const timeMMSS = computed(() => {
  let minutes = Math.floor(props.timeMs/1000/60);
  let seconds = Math.floor((props.timeMs/1000)) % 60;
  minutes = minutes < 10 ? `0${minutes}` : minutes;
  seconds = seconds < 10 ? `0${seconds}` : seconds;
  return `${minutes}:${seconds}`;
})

</script>

<template>
  <div class="song">
    <button @click="" >play</button>
    <span>{{ index }}</span>
    <span>{{ name }}</span>
    <span>{{ timeMMSS }}</span>
  </div>
</template>

<style scoped>
.song {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
</style>
