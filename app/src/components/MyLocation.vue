<template>
    <div>
      <p v-if="error">{{ error }}</p>
      <p v-else-if="loading">Loading...</p>
      <p v-else-if="position">Latitude: {{ position.coords.latitude }}, Longitude: {{ position.coords.longitude }}</p>
      <button @click="getUserLocation">Get User Location</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        loading: false,
        error: '',
        position: null,
      };
    },
    methods: {
      getUserLocation() {
        this.loading = true;
        if ("geolocation" in navigator) {
          navigator.geolocation.getCurrentPosition(
            (position) => {
              this.loading = false;
              this.position = position;
            },
            (error) => {
              this.loading = false;
              this.error = `Error getting user location: ${error.message}`;
            }
          );
        } else {
          this.loading = false;
          this.error = 'Geolocation is not supported.';
        }
      },
    },
  };
  </script>
  