<script>
import { store } from "../../data/store";

import CardDetail from "./CardDetail.vue";

export default {
  data() {
    return {
      title: "Cards List",
      store
    };
  },

  components: { CardDetail },
};
</script>

<template>
  <h2>{{ title }}</h2>

  <ul>
    <li  v-for="movie in movies" :key="movie.id">
      {{ movie.title }} - {{ movie.original_title }} - {{ movie.language }} -
      {{ movie.vote }}
    </li>
  </ul>
  <CardDetail />
</template>

<style lang="scss" scoped></style>
