<template>
  <v-card class="mx-auto" max-width="374">
    <v-img
      height="150"
      src="https://picsum.photos/id/11/500/300"
    ></v-img>

    <v-card-title>{{ location.name }}</v-card-title>

    <v-card-actions>
      <v-btn @click="filmDirection" color="orange" text>Film</v-btn>
      <nuxt-link :to="`locationCard/${location.id}`">More</nuxt-link>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
    name: "Locations",

    props: {
        location: {
            required: true,
            films: {}
        }
    },

    methods: {
        filmDirection() {
            
            const url = this.location.films;

            for (let i = 0; i < url.length; i++) {
                const element = url[i];
                const id = element.substring(element.lastIndexOf('/') + 1);
                this.film = id;

                this.$router.replace({
                path: "/movieCard/" + `${this.film}`
                });
            }
        }
    }
}
</script>