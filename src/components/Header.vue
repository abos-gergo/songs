<script setup lang="ts">
import { defineEmits, ref } from 'vue';

// Define the emit for the component
const emit = defineEmits<{
  (event: 'updateFilter', value: string): void;
}>();

// Define the model for the filterText
const filterText = defineModel<string>();

defineProps<{
  filterText: string;
}>();

// Watch for changes in the input and emit an event
const updateFilter = (value: string) => {
  emit('updateFilter', value);
};
</script>

<template>
  <div class="header">
    <h1>Songs</h1>
    <input type="text" v-model="filterText" @input="updateFilter($event.target.value)" placeholder="Search for songs..."
      class="search-box" />
    <ul class="song-list">
      <li v-for="song in filteredSongs" :key="song.id">
        {{ song.name }}
      </li>
    </ul>
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
