<template>
  <div>
    <v-app-bar color="cyan accent-4" flat dark>
      <!--<v-app-bar-nav-icon></v-app-bar-nav-icon>-->

      <v-toolbar-title>
        <nuxt-link to="/">GhibliNuxt</nuxt-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <nuxt-link to="/">Movies</nuxt-link>

      <v-spacer></v-spacer>

      <nuxt-link to="/peoples">Peoples</nuxt-link>

      <v-spacer></v-spacer>

      <nuxt-link to="/locations">Locations</nuxt-link>

      <v-spacer></v-spacer>
      
      <nuxt-link to="/about">About us</nuxt-link>

      <v-spacer></v-spacer>

      <v-autocomplete
            hide-no-data
            hide-selected
            filled
            clearable
            prepend-icon="mdi-search"
            label="Search"
            :items="movies"
            item-text="title"
            item-value="id"
            id="search"
        >
        <template v-slot:item="{item}">
                <v-btn text :to="`/movieCard/${item.id}`">{{item.title}}</v-btn>
            </template>
      </v-autocomplete>
    </v-app-bar>
  </div>
</template>

<script>
export default {
    name: "Navbar",

    data() {
      return {
        movies: [],
        search: null,
      }
    },

    async fetch() {
    const api = "https://ghibliapi.herokuapp.com/films";
    this.movies = await this.$axios.$get(api);
  }
}
</script>

<style scoped>
a, a.nuxt-link-active {
  font-weight: bold;
  color: aliceblue;
}

a.nuxt-link-exact-active {
  color: #C51162;
}

a,
a:visited {
  text-decoration: none;
}

a:hover {
  color: #C51162;
}
</style>