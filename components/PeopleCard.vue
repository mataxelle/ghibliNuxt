<template>
  <v-card class="mx-auto my-12" max-width="400">
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
      <v-btn @click="filmDirection" color="orange" text>Film</v-btn>

      <v-btn color="orange" text> Species </v-btn>
    </v-card-actions>
  </v-card>
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