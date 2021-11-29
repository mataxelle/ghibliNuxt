<template>
  <v-card class="mx-auto" max-width="400" height="100%" hover>
    <v-img
      height="150"
      src="https://picsum.photos/id/11/500/300"
    ></v-img>

    <v-card-title>{{ vehicle.name }}</v-card-title>

    <v-card-text>
        <p>Vehicle class : {{ vehicle.vehicle_class }}</p>
        <p>Length : {{ vehicle.length }}</p>
        <p>Description : {{ vehicle.description }}</p>
    </v-card-text>

    <v-card-actions>
      <v-btn @click="filmDirection" color="orange" text>Film</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
    name: "Vehicles",

    props: {
        vehicle: {
            required: true,
        }
    },

    methods: {
        filmDirection() {
            
            const url = this.vehicle.films;

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