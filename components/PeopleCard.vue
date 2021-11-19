<template>
  <div>
    <div class="row">
      <div class="col">
        <v-card class="mx-auto my-12">
          <v-img
            class="white--text align-end"
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
          >
            <v-card-title>{{ people.name }}</v-card-title>
          </v-img>

          <v-card-text class="text--primary">
            <p>Gender : {{ people.gender }}</p>
            <p>Age : {{ people.age }}</p>
            <p>Eye color : {{ people.eye_color }}</p>
            <p>Hair color : {{ people.hair_color }}</p>
          </v-card-text>

          <v-card-actions>
            <v-btn @click="home" color="orange" text>Home</v-btn>
          </v-card-actions>
        </v-card>
      </div>
    </div>

    <div class="row">
      <div class="col">
        <h3 class="mb-6">Film</h3>
        <div class="row">
          <div
            class="col-md-4 col-sm-6"
            v-for="film in people.films"
            :key="film.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text class="btn" @click="film">Film</v-btn>
          </div>
        </div>
      </div>
      <div class="col">
        <h3 class="mb-6">Specie</h3>
        <div class="row">
          <div
            class="col-md-4 col-sm-6"
            v-for="specie in people.species"
            :key="specie.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text class="btn" @click="specieDirection">Specie</v-btn>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PeopleCard",

  data() {
    return {
      people: {},
    };
  },

  async fetch() {
    const apiPeople =
      "https://ghibliapi.herokuapp.com/people/" + this.$route.params.id;
    this.people = await this.$axios.$get(apiPeople);
  },

  methods: {
    filmDirection() {
      const url = this.people.films;
      console.log(url);

      for (let i = 0; i < url.length; i++) {
        const element = url[i];
        const id = element.substring(element.lastIndexOf("/") + 1);
        this.film = id;

        this.$router.replace({
          path: "/movieCard/" + `${this.film}`,
        });
      }
    },
  },
};
</script>