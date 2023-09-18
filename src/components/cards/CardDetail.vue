<script>
export default {
  props: {
    cardInfo: Object,
  },

  computed: {
    hasFlag() {
      const allowedFlags = ["en", "it"];
      return allowedFlags.includes(this.cardInfo.language);
    },

    flagSrc() {
      const flagUrl = new URL(
        `../../assets/img/${this.cardInfo.language}.png`,
        import.meta.url
      );
      return flagUrl.href;
    },

    posterSrc() {
      const poster = {
        baseUrl: "https://image.tmdb.org/t/p",
        size: "/w342",
      };
      return `${poster.baseUrl}${poster.size}${this.cardInfo.posterPath}`;
    },
  },
};
</script>

<template>
  <div class="card">
    <div class="card-body">
      <ul>
        <li>{{ cardInfo.title }}</li>
        <li>{{ cardInfo.original_title }}</li>
        <li v-if="hasFlag" class="bandiera">
          <img :src="flagSrc" :alt="cardInfo.language" />
        </li>
        <li>{{ cardInfo.vote }}</li>
        <li>
          <img :src="posterSrc" :alt="cardInfo.title" />
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.bandiera {
  img {
    height: 50px;
  }
}
</style>
