<template>
  <div>
    <div class="row">
      <div class="col">
        <h1 class="text-center my-6">{{ movie.title }}</h1>
        <v-card class="mx-auto my-12">
          <v-img :src="movie.image"></v-img>
          <v-card-title>{{ movie.title }}</v-card-title>
          <v-card-subtitle>
            {{ movie.original_title }} -
            {{ movie.original_title_romanised }}
          </v-card-subtitle>

          <v-card-text>
            <v-row align="center" class="">
              <v-col>
                <span> Score : {{ movie.rt_score }}% </span>
              </v-col>
            </v-row>

            <v-row>
              <v-col>
                <p>Release date : {{ movie.release_date }}</p>
                <p>Running time : {{ movie.running_time }}mn</p>
              </v-col>
            </v-row>

            <v-row>
              <v-col>
                {{ movie.description }}
              </v-col>
            </v-row>
          </v-card-text>

          <v-divider class="mx-4"></v-divider>

          <v-card-title>Production</v-card-title>

          <v-card-text>
            <div class="my-4 text-subtitle-1">
              Director : {{ movie.director }}
            </div>
            <div class="my-4 text-subtitle-1">
              Productor : {{ movie.producer }}
            </div>
          </v-card-text>

          <v-card-actions>
            <v-btn @click="home" color="deep-purple lighten-2" text>
              HOME
            </v-btn>
          </v-card-actions>
        </v-card>
      </div>
    </div>

    <div class="row mb-6">
      <div class="col-md-6 col-xs">
        <h3 class="mb-6 text-center">Related characters</h3>
        <div class="row">
          <div
            class="col-sm-4 col"
            v-for="people in movie.people"
            :key="people"
          >
            <div class="pa-7 red darken-2 rounded-circle d-inline-block"></div>
            <v-btn text @click="peopleDirection">people</v-btn>
          </div>
        </div>
      </div>

      <div class="col-md-6 col-xs">
        <h3 class="mb-6 text-center">Related species</h3>
        <div class="row">
          <div
            class="col-sm-4 col"
            v-for="specie in movie.species"
            :key="specie.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text @click="specieDirection">specie</v-btn>
          </div>
        </div>
      </div>
    </div>

    <div class="row mb-6">
      <div class="col-md-6 col-xs">
        <h3 class="mb-6 text-center">Related locations</h3>
        <div class="row">
          <div
            class="col-sm-4 col"
            v-for="location in movie.locations"
            :key="location.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text @click="locationDirection">location</v-btn>
          </div>
        </div>
      </div>
      <div class="col-md-6 col-xs">
        <h3 class="mb-6 text-center">Related vehicles</h3>
        <div class="row">
          <div
            class="col-sm-4 col"
            v-for="vehicle in movie.vehicles"
            :key="vehicle.id"
          >
            <div class="pa-7 cyan darken-3 rounded-circle d-inline-block"></div>
            <v-btn text @click="vehicleDirection">vehicle</v-btn>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",

  data() {
    return {
      movie: {},
    };
  },

  async fetch() {
    const oneMovie =
      `https://ghibliapi.herokuapp.com/films/` + this.$route.params.id;
    this.movie = await this.$axios.$get(oneMovie);
  },

  methods: {
    home() {
      this.$router.push("/");
    },

    peopleDirection() {
      const url = this.movie.people;
      for (let i = 0; i < url.length; i++) {
        const element = url[i];

        const id = element.substring(element.lastIndexOf("/") + 1);
        //this.resident = id;
        console.log(id);
        
        if (!id) {
          this.$router.push("/peoples");
        } else {
          this.$router.replace({ path: "/peopleCard/" + id });
        }
        
        /*this.$router.replace({
          path: "/peopleCard/" + `${this.resident}`,
        });*/
      }
    },

    locationDirection() {
      this.$router.push("/locations");
    },

    vehicleDirection() {
      this.$router.push("/vehicles");
    },

    specieDirection() {
      this.$router.push("/species");
    },
  },
};
</script>