<script>
import { store } from "./data/store";
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

const api_key = "c1d46a13d18121bd8fc7c9da7083f0ba";

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
            api_key,
          },
        })
        .then((res) => {
          store.movies = res.data.results.map((movie) => {
            const {
              id,
              title,
              original_title,
              original_language,
              vote_average,
            } = movie;
            return {
              id,
              title,
              original_title,
              language: original_language,
              vote: Math.ceil(vote_average / 2),
            };
          });
        });
    },
  },
};
</script>

<template>
  <AppHeader @start-search="fetchMovies" />
  
  <AppMain />
</template>

<style lang="scss"></style>
