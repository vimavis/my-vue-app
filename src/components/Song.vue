<script setup>
import { computed } from 'vue'

const props = defineProps({
  index: Number,
  name: String,
  timeMs: Number,
  active: Boolean
})

const timeMMSS = computed(() => {
  const minutes = Math.floor(props.timeMs/1000/60);
  const seconds = Math.floor((props.timeMs/1000)) % 60;
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
  display: flex;
  justify-content: space-around;
}
</style>
