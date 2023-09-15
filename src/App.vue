<script>
import { store } from "./data/store";
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      movies: [],
    };
  },

  components: { AppHeader, AppMain },

  methods: {
    fetchMovies(term) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            query: term,
            api_key: "c1d46a13d18121bd8fc7c9da7083f0ba",
          },
        })
        .then((res) => {
          this.movies = res.data.results;
        });
    },
  },

  created() {
    this.fetchMovies();
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

<style lang="scss"></style>
