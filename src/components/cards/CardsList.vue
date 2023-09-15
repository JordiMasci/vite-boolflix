<script>
import { store } from "../../data/store";

import CardDetail from "./CardDetail.vue";

export default {
  data() {
    return {
      title: "Cards List",
      store,
    };
  },

  components: { CardDetail },
};
</script>

<template>
  <h2>{{ title }}</h2>
  <CardDetail v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"/>
</template>

<style lang="scss" scoped></style>
