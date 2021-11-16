<template>
  <div class="container">
    <div class="row">
      <div class="col-10 offset-1">
        <LocationCard />
      </div>
    </div>
  </div>
</template>

<script>
import LocationCard from "@/components/LocationCard.vue";

export default {
  components: {
    LocationCard,
  },
};
</script>