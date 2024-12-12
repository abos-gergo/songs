<template>
  <tr>
    <td class="song-title">{{ song.TITLE }}</td>
    <td>{{ artist.artist }}</td>
    <td>{{ song.YEAR }}</td>
    <td>{{ song.BPM }}</td>
    <td>{{ song.GENRE }}</td>
    <td>{{ song.TIME }}</td>
    <td>{{ artist.fame }}</td>
    <td>{{ artist.popularity }}</td>
  </tr>
</template>


<script>
export default {
  props: {
    song: {
      type: Object,
      required: true,
    },
    artists: {
      type: Array,
      required: true,
    }
  },
  computed: {
    artist() {
      // Find the artist with the matching ARTIST_ID from the artists array
      return this.artists.find(artist => artist._id === this.song.ARTIST_ID);
    }
  }
};
</script>

<style scoped></style>
