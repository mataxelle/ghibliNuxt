<template>
  <div>
    <div class="row">
      <div class="col">
        <v-card class="mx-auto my-12">
          <v-img height="200" src="https://picsum.photos/id/11/500/300"></v-img>

          <v-card-title>{{ location.name }}</v-card-title>

          <v-card-text>
            <p>Climate : {{ location.climate }}</p>
            <p>Terrain : {{ location.terrain }}</p>
            <p>Surface water : {{ location.surface_water }}</p>
          </v-card-text>
        </v-card>
      </div>
    </div>

    <div class="row mb-6">
      <div class="col">
        <h3 class="mb-6">Related film</h3>
        <div class="row">
          <div
            class="col-md-4 col-sm-6"
            v-for="film in location.films"
            :key="film.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn class="btn" @click="filmDirection">Film</v-btn>
          </div>
        </div>
      </div>
      <div class="col-md-6 col-xs">
        <h3 class="mb-6">Related characters</h3>
        <div class="row">
          <div
            class="col-md-4 col-sm-6"
            v-for="resident in location.residents"
            :key="resident"
          >
            <div class="pa-7 red darken-2 rounded-circle d-inline-block"></div>
              <v-btn @click="peopleDirection">hello</v-btn>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LocationCard",

  data() {
    return {
      location: {},
    };
  },

  async fetch() {
    const oneLocation =
      `https://ghibliapi.herokuapp.com/locations/` + this.$route.params.id;
    this.location = await this.$axios.$get(oneLocation);
  },

  methods: {
    filmDirection() {
      const url = this.location.films;

      for (let i = 0; i < url.length; i++) {
        const element = url[i];
        const id = element.substring(element.lastIndexOf("/") + 1);
        this.film = id;

        this.$router.replace({
          path: "/movieCard/" + `${this.film}`,
        });
      }
    },

    peopleDirection() {
      const url = this.location.residents;

      for (let i = 0; i < url.length; i++) {
        const element = url[i];
        const id = element.substring(element.lastIndexOf("/") + 1);
        //this.resident = id;
        console.log(id);
        
        /*this.$router.replace({
          path: "/peopleCard/" + `${this.resident}`,
        });*/
      }
    },
  },
};
</script>