<template>
  <v-card class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>{{ people.name }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">ici : {{ people.films }}</v-card-subtitle>

    <v-card-text class="text--primary">
      <p>{{ people.gender }}</p>
      <p>{{ people.age }}</p>
      <p>{{ people.eye_color }}</p>
      <p>{{ people.hair_color }}</p>
    </v-card-text>

    <v-card-actions>
      <v-btn @click="filmDirection" color="orange" text>Film</v-btn>

      <v-btn color="orange" text> Species </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
    name: "People",

    props: {
        people: {
            required: true,
            films: ''
        }
    },

    methods: {
        filmDirection() {
            
            const url = this.people.films;
            console.log(url);
            //const url = "https://ghibliapi.herokuapp.com/films/dc2e6bd1-8156-4886-adff-b39e6043af0c";
            const id = url.substring(url.lastIndexOf('/') + 1);
            console.log(id);
            //const result = filmId.searchParams.get()
            //console.log(result);
        }
    }
}
</script>