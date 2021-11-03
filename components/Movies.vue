<template>
  <div class="row">
    <v-card v-for="movie in movies" :key="movie.id" :loading="loading" class="col mx-auto my-12" max-width="374">

      <v-img
        height="150"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      ></v-img>

      <v-card-title>{{ movie.title }}</v-card-title>
      <v-card-subtitle>{{ movie.original_title }} - {{ movie.original_title_romanised }}</v-card-subtitle>

      <v-card-text>
        <div class="my-4 text-subtitle-1">Director : {{ movie.director }}</div>
        <div class="my-4 text-subtitle-1">Productor : {{ movie.producer }}</div>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>

      <v-card-text>
        <p>Release date : {{ movie.release_date }}</p>
      </v-card-text>

      <v-card-actions>
        <nuxt-link color="deep-purple lighten-2" text to="/movieCard">
          More
        </nuxt-link>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "Movies",

  data() {
      return {
          movies: {}
      }
  },

  mounted() {
      axios
        .get('https://ghibliapi.herokuapp.com/films')
        .then(response => (this.movies = response.data))
        .catch(error => {
            console.log(error)
        })
  },

  /*methods: {
    movieLink() {
      axios
    }
  }*/
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>