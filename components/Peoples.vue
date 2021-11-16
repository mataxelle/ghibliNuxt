<template>
  <v-card class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
    </v-img>

    <v-card-title>
      <nuxt-link :to="`/peopleCard/${people.id}`">{{ people.name }}</nuxt-link>
    </v-card-title>

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
      films: {},
    },
  },

  methods: {
    filmDirection() {
      const url = this.people.films;

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