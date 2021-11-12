<template>
  <div class="row">
    <div class="col">
      <v-card class="mx-auto my-12" max-width="374">
        <v-img
          height="250"
          src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
        ></v-img>

        <v-card-title>{{ movie.title }}</v-card-title>
        <v-card-subtitle>
          {{ movie.original_title }} -
          {{ movie.original_title_romanised }}
        </v-card-subtitle>

        <v-card-text>
          <v-row align="center" class="">
            <v-col>
              <v-rating
                color="amber"
                dense
                half-increments
                readonly
                size="14"
              ></v-rating>
            </v-col>
            <v-col>
              <span class="gray--text ml-n7">
                {{ movie.rt_score }}% | {{ movie.release_date }}
              </span>
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
          <v-btn color="deep-purple lighten-2">
            Reserve
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";

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
};
</script>