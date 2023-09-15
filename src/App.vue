<script>
import { store } from "./data/store";
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: { AppHeader, AppMain },

  methods: {
    fetchMovies(queryString) {
      axios.get("").then((res) => {});
    },
  },

  created() {
    // this.fetchMovies
  },
};
</script>

<template>
  <AppHeader @start-search="fetchMovies" />
  <ul>
    <li v-for="movie in movies" :key="movie.id">
      {{ movie.title }} - {{ movie.original_title }} -
      {{ movie.original_language }} - {{ movie.vote_average }} -
    </li>
  </ul>
  <AppMain />
</template>

<style lang="scss">

</style>
