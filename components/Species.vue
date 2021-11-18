<template>
  <v-card class="mx-auto" width="400">

    <v-card-title>{{ specie.name }}</v-card-title>

    <v-card-actions>
      <v-btn color="orange" text>Film</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
    name: "Species",

    props: {
        specie: {
            required: true
        }
    }
}
</script>