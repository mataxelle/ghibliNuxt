<template>
  <div>
    <v-app-bar color="deep-purple accent-4" flat dark>
      <!--<v-app-bar-nav-icon></v-app-bar-nav-icon>-->

      <v-toolbar-title>GhibliNuxt</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn text>Films</v-btn>
      
      <v-btn text>Contact</v-btn>

      <v-spacer></v-spacer>

      <v-autocomplete
            v-model="value"
            :items="items"
            filled
            clearable
            prepend-icon="mdi-search"
            label="Recherche"
        >
      </v-autocomplete>
    </v-app-bar>
  </div>
</template>

<script>
export default {
    name: "Navbar"
}
</script>