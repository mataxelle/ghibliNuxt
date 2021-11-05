<template>
  <div class="row">
    <div v-if="$fetchState.error" class="col text-center">
      <p>Error while fetching mountains</p>
    </div>
    <div v-else class="col-md-4 col-sm" v-for="movie in movies" :key="movie.id">
      <v-card class="mx-auto my-12" max-width="374">
        <v-img
          height="150"
          src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
        ></v-img>

        <v-card-title>{{ movie.title }}</v-card-title>

        <v-card-text>
          <v-row align="center" class="">
            <v-col class="col-5">
              <v-rating
                :value="movie.rt_score"
                color="amber"
                dense
                half-increments
                readonly
                size="14"
              ></v-rating>
            </v-col>
            <v-col>
              <div class="gray--text ml-n7">
                {{ movie.rt_score }}%
              </div>
            </v-col>
          </v-row>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>

        <v-card-text>
          <p>Date de sortie : {{ movie.release_date }}</p>
        </v-card-text>

        <v-card-actions>
          <nuxt-link
            color="deep-purple lighten-2"
            text
            :to="{ name: 'movieCard', params: { id: movie.id } }"
          >
          <!--:to="{ name: 'movieCard', params: { id: movie.id } }"-->
            More
          </nuxt-link>
        </v-card-actions>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  name: "Movies",

  data() {
    return {
      movies: {}
    }
  },

  async fetch() {
    const api = 'https://ghibliapi.herokuapp.com/films'
    this.movies = await this.$axios.$get(api)
  }
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>