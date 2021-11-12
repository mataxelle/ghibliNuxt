<template>
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
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>
        </v-col>
        <v-col>
          <div class="gray--text ml-n7">{{ movie.rt_score }}%</div>
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
</template>

<script>
export default {
  name: "Movies",

  props: {
    movie: {
      required: true,
    }
  }  
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>