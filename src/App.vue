<script setup>
import Song from "./components/Song.vue";
import { onMounted, ref } from 'vue'

const listSongs = ref([]);
const status = ref('loading');

onMounted(async () => {
  const url = 'https://musicbrainz.org/ws/2/release/b84ee12a-09ef-421b-82de-0441a926375b?inc=recordings&fmt=json';
  try {
    const response = await (await fetch(url)).json();
    listSongs.value = response.media[0].tracks.map((song) => {
      return {
        index: song.position,
        name: song.title,
        timeMs: song.length,
        active: false,
      };
    });
    status.value = 'ok';
  } catch (error) {
    status.value = 'error';
  }
})

</script>

<template>
  <div class="container">
    <div class="border">album</div>
    <div class="border">
      <div class="headers">
        <span></span>
        <span>#</span>
        <span>Nombre</span>
        <span>Duracion</span>
      </div>
      <song
        v-for="song in listSongs"
        :index="song.index"
        :name="song.name"
        :time-ms="song.timeMs"
        :active="false"
      ></song>
    </div>
  </div>
</template>

<style scoped>
.container {
  height: 100vh;
  width: 100vw;
  display: grid;
  grid-template-rows: 100px 1fr;
}

.border {
  border: solid 2px red;
}

.headers {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
</style>
