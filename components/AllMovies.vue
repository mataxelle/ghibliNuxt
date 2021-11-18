<template>
    <div>
        <h1 class="text-center my-6">All movies</h1>

        <div class="row my-6">
            <div v-if="$fetchState.error" class="col text-center">
                <p>Error while fetching mountains</p>
            </div>
            <div v-else class="col-lg-4 col-sm mx-auto" v-for="movie in movies" :key="movie.id">
                <Movies :movie="movie" />
            </div>
        </div>
    </div>    
</template>

<script>
import Movies from "@/components/Movies.vue";

export default {
  components: {
    Movies,
  },

  data() {
    return {
      movies: [],
    };
  },

  async fetch() {
    const api = "https://ghibliapi.herokuapp.com/films";
    this.movies = await this.$axios.$get(api);
  },
};
</script>