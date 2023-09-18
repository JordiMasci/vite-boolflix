<script>
import { store } from "../../data/store";

import CardDetail from "./CardDetail.vue";

export default {
  data() {
    return {
      title: "Movies",
      title2: "Tv Series",
      store,
    };
  },

  components: { CardDetail },
};
</script>

<template>
  <h2>{{ title }}</h2>
  <CardDetail v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"/>

  <h2>{{ title2 }}</h2>
  <CardDetail v-for="tvSeri in store.tvSerie" :key="tvSeri.id" :cardInfo="tvSeri"/>
</template>

<style lang="scss" scoped></style>
