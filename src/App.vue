<script setup lang="ts">
import Header from './components/Header.vue';
import { ref } from 'vue';
import artistData from './artistData.ts';
import songData from './songData.ts';
import SongRow from './components/SongRow.vue';

let songs = ref([...songData]); // Initialize as a reactive reference

const updateSongs = ([title, artist]: [string, string]) => {
  console.log(title.value.toLowerCase());
  console.log(artist.value.toLowerCase());

  songs.value = songData.filter((song) => {
    const a = artistData.find((a) => a._id === song.ARTIST_ID);
    return (
      song.TITLE.toLowerCase().includes(title.value.toLowerCase()) &&
      (a?.artist.toLowerCase() || '').includes(artist.value.toLowerCase())
    );
  });

};
</script>

<template>
  <Header @update-filter="updateSongs"></Header>

  <main>
    <table id="songs">
      <tbody>
        <tr>
          <th>Title</th>
          <th>Artist</th>
          <th>Year</th>
          <th>BPM</th>
          <th>Genre</th>
          <th>Time</th>
          <th>Artist fame</th>
          <th>Artist popularity</th>
        </tr>
        <SongRow v-for="song in songs" :key="song._id" :song="song" :artists="artistData"></SongRow>
      </tbody>
    </table>
  </main>
</template>

<style scoped>
#songs {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
  font-size: 16px;
  text-align: left;
}

#songs th,
#songs td {
  padding: 12px 15px;
  border: 1px solid #ddd;
}

#songs th {
  background-color: #f4f4f4;
  color: #333;
  font-weight: bold;
}

#songs tr:nth-child(even) {
  background-color: #f9f9f9;
}

#songs tr:hover {
  background-color: #f1f1f1;
}

#songs td {
  color: #555;
}

#songs th:first-child,
#songs td:first-child {
  text-align: left;
}

#songs {
  border: 1px solid #ccc;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
</style>
