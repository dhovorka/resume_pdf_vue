<template>
  <div class="container">
    <h1>All Photos</h1>
    <div v-for="photo in photos">
      <h2>{{ photo.name }}</h2>
      <img v-bind:src="photo.url">
      <p>Width: {{ photo.width }}</p>
      <p>Height: {{ photo.height }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      photos: [
        {
          name: "doggies",
          url:
            "https://static.scientificamerican.com/sciam/cache/file/D059BC4A-CCF3-4495-849ABBAFAED10456_source.jpg?w=590&h=800&526ED1E1-34FF-4472-B348B8B4769AB2A1"
        }
      ]
    };
  },
  created: function() {
    axios.get("/api/photos").then(response => {
      this.photos = response.data;
    });
  },
  methods: {}
};
</script>
