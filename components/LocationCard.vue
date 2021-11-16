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
            <p>residents : {{ location.residents }}</p>
          </v-card-text>

          <v-card-actions>
            <v-btn color="orange" text>Film</v-btn>
          </v-card-actions>
        </v-card>
      </div>
    </div>

    <div class="row">
      <div
        class="col"
        v-for="resident in location.residents"
        :key="resident.id"
      >
        <Residents :resident="resident" />
      </div>
    </div>
  </div>
</template>

<script>
import Residents from "@/components/Residents.vue";

export default {
  name: "LocationCard",

  components: {
    Residents,
  },

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

  /*async fetch() {
    const locatonResident = this.location.residents;
    this.residents = await this.$axios.$get(locatonResident);
  }*/
};
</script>