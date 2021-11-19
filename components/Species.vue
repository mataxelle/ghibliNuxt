<template>
  <v-card class="mx-auto" max-width="400">
    <v-sheet color="cyan darken-3">
      <v-btn text block @click="specieInformation" height="200">
        <v-card-title class="white--text text-h5">{{ specie.name }}</v-card-title>
      </v-btn>
    </v-sheet>
  </v-card>
</template>

<script>
export default {
  name: "Species",

  props: {
    specie: {
      required: true,
    },
  },

  methods: {
    specieInformation() {
      this.$router.push("/specieCard/" + this.specie.id);
    },
  },
};
</script>