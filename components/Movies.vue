<template>
  <v-card class="mx-auto" max-width="400">
    <nuxt-link
        color="deep-purple lighten-2"
        text
        :to="`/movieCard/${movie.id}`"
    >
      <v-img
      height="200"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
    ></v-img>
    </nuxt-link>

    <v-card-title>{{ movie.title }}</v-card-title>

    <v-card-text>
      <span>Score : {{ movie.rt_score }}%</span>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-text>
      <p>Release date : {{ movie.release_date }}</p>
    </v-card-text>

    <v-card-actions>
      <v-btn @click="filmDirection" text color="cyan darken-3">More</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "Movies",

  props: {
    movie: {
      required: true,
    }
  },

  methods: {
    filmDirection() {
      this.$router.push('/movieCard/' + this.movie.id)
    }
  }
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>