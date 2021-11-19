<template>
  <div>
    <div class="row">
      <div class="col">
        <v-card class="mx-auto my-12" max-width="400">
          <v-img
            class="white--text align-end"
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
          >
            <v-card-title>{{ specie.name }}</v-card-title>
          </v-img>

          <v-card-text class="text--primary">
            <p>Classification : {{ specie.classification }}</p>
            <p>Eye colors : {{ specie.eye_colors }}</p>
            <p>Hair colors : {{ specie.hair_colors }}</p>
          </v-card-text>

          <v-card-actions>
            <v-btn @click="home" color="orange" text>Home</v-btn>
          </v-card-actions>
        </v-card>
      </div>
    </div>

    <div class="row mb-6">
      <div class="col">
        <h3 class="mb-6">Related characters</h3>
        <div class="row">
          <div class="col-3" v-for="people in specie.people" :key="people.id">
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text class="btn" @click="characterDirection">characters</v-btn>
          </div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col">
        <h3 class="mb-6">Related films</h3>
        <div class="row">
          <div class="col-3" v-for="film in specie.films" :key="film.id">
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text class="btn" @click="filmDirection">Film</v-btn>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SpecieCard",

  data() {
    return {
      specie: {},
    };
  },

  async fetch() {
    const apiSpecie =
      "https://ghibliapi.herokuapp.com/species/" + this.$route.params.id;
    this.specie = await this.$axios.$get(apiSpecie);
  },

  methods: {
    home() {
        this.$router.push('/');
    },

    characterDirection() {
        this.$router.push('');
    },

    filmDirection() {
        this.$router.push('');
    }
  },
};
</script>