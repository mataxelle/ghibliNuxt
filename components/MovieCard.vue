<template>
  <div class="row">
    <div class="col">
      <v-card class="mx-auto my-12" max-width="600">
        <v-card-title>{{ movie.title }}</v-card-title>
        <v-card-subtitle>
          {{ movie.original_title }} -
          {{ movie.original_title_romanised }}
        </v-card-subtitle>

        <v-card-text>
          <v-row align="center" class="">
            <v-col>
              <span> Score : 
                {{ movie.rt_score }}%
              </span>
            </v-col>
          </v-row>

          <v-row>
            <v-col>
              <p>Release date : {{ movie.release_date }}</p>
              <p>Running time : {{ movie.running_time }}mn</p>
            </v-col>
          </v-row>

          <v-row>
            <v-col>
              {{ movie.description }}
            </v-col>
          </v-row>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>

        <v-card-title>Production</v-card-title>

        <v-card-text>
          <div class="my-4 text-subtitle-1">
            Director : {{ movie.director }}
          </div>
          <div class="my-4 text-subtitle-1">
            Productor : {{ movie.producer }}
          </div>
        </v-card-text>
        
        <v-card-actions>
          <v-btn @click="characters" color="deep-purple lighten-2" text>
            CHARACTERS
          </v-btn>
          <v-btn @click="locations" color="deep-purple lighten-2" text>
            LOCATION
          </v-btn>
          <v-btn @click="home" color="deep-purple lighten-2" text>
            HOME
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",

  data() {
    return {
      movie: {},
    };
  },

  async fetch() {
    const oneMovie = `https://ghibliapi.herokuapp.com/films/` + this.$route.params.id;
    this.movie = await this.$axios.$get(oneMovie);
  },

  methods: {
    home() {
      this.$router.push("/")
    },

    characters() {
      this.$router.push("/peoples")
    },

    locations() {
      this.$router.push("/locations")
    }
  }
};
</script>