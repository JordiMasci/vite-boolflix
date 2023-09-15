<script>
import CardsList from "./cards/CardsList.vue";

export default {
  components: { CardsList },

  data() {
    return {
      title: "App Main",
    };
  },
};
</script>

<template>
  <div class="container mt-5">
    <h1>{{ title }}</h1>
     <CardsList />
  </div>
</template>

<style lang="scss" scoped></style>
