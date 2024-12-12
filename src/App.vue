<script setup lang="ts">
import Header from './components/Header.vue';
import { ref } from 'vue';
import artistData from './artistData.ts';
import songData from './songData.ts';
import SongCard from './components/SongCard.vue';

// Use `ref` for reactive data
let filterText = ref("");
let songs = ref([...songData]); // Initialize as a reactive reference

// Update songs list based on filter
const updateSongs = () => {
  songs.value = songData.filter((s) =>
    s.TITLE.toLowerCase().includes(filterText.value.toLowerCase())
  );
};
</script>

<template>
  <Header v-model="filterText" @update-filter="updateSongs()"></Header>

  <main>
    <div id="songs">
      <SongCard v-for="song in songs" :key="song._id" :song="song" :artists="artistData"></SongCard>
    </div>
  </main>
</template>

<style scoped>
#songs {
  display: flex;
  flex-wrap: wrap;
}
</style>
