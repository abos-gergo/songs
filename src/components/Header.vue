<script setup lang="ts">
import { defineEmits, ref } from 'vue';

const emit = defineEmits<{
  (event: 'updateFilter', value: [string, string]): void;
}>();

let filterTitle = ref("")
let filterArtist = ref("")

const updateFilter = () => {
  emit('updateFilter', [filterTitle, filterArtist]);
};
</script>

<template>
  <div class="header">
    <h1>Songs</h1>
    <input type="text" v-model="filterTitle" @input="updateFilter()" placeholder="Search for songs..."
      class="search-box" />
    <input type="text" v-model="filterArtist" @input="updateFilter()" placeholder="Search for artists..."
      class="search-box" />
  </div>
</template>

<style scoped>
.header {
  padding: 20px;
  background-color: #f3f4f6;
  border-bottom: 2px solid #e0e0e0;
}

h1 {
  margin: 0;
  font-size: 2rem;
  color: #333;
}

.search-box {
  margin-top: 10px;
  padding: 8px;
  width: 100%;
  max-width: 300px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 1rem;
  margin-right: 2%;
}

.song-list {
  margin-top: 20px;
  list-style-type: none;
  padding: 0;
}

.song-list li {
  margin-bottom: 8px;
  font-size: 1.1rem;
  color: #333;
}
</style>
