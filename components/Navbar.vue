<template>
  <div>
    <v-app-bar color="deep-purple accent-4" flat dark>
      <!--<v-app-bar-nav-icon></v-app-bar-nav-icon>-->

      <v-toolbar-title>
        <nuxt-link to="/">GhibliNuxt</nuxt-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <nuxt-link to="##">Films</nuxt-link>

      <v-spacer></v-spacer>
      
      <nuxt-link to="/about">Contact</nuxt-link>

      <v-spacer></v-spacer>

      <v-autocomplete
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

<style scoped>
a, a.nuxt-link-active {
  font-weight: bold;
  color: aliceblue;
}

a.nuxt-link-exact-active {
  color: #da73cc;
}

a,
a:visited {
  text-decoration: none;
}

a:hover {
  color: #da73cc;
}
</style>