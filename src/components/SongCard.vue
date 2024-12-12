<template>
  <div class="song-card">
    <h2 class="song-title">{{ song.TITLE }}</h2>
    <p class="song-details">
      <strong>Artist:</strong> {{ artist ? artist.artist : 'Unknown' }}<br />
      <strong>Year:</strong> {{ song.YEAR }}<br />
      <strong>BPM:</strong> {{ song.BPM }}<br />
      <strong>Genre:</strong> {{ song.GENRE }}<br />
      <strong>Time:</strong> {{ song.TIME }}
    </p>
    <div class="artist-info">
      <strong>Artist Fame:</strong> {{ artist ? artist.fame : 'N/A' }}<br />
      <strong>Artist Popularity:</strong> {{ artist ? artist.popularity : 'N/A' }}
    </div>
  </div>
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

<style scoped>
.song-card {
  border: 1px solid #ddd;
  padding: 20px;
  margin: 10px;
  border-radius: 8px;
  background-color: #f9f9f9;
  width: 300px;
}

.song-title {
  font-size: 1.5rem;
  margin: 0 0 10px;
}

.song-details {
  font-size: 1rem;
  margin-bottom: 15px;
}

.artist-info {
  font-size: 0.9rem;
  color: #555;
}

strong {
  font-weight: bold;
}
</style>
