<template>
    <div class="container">
    <div class="row">
      <div class="col-10 offset-1">
        <MovieCard />
      </div>
    </div>
  </div>
</template>

<script>
import MovieCard from '@/components/MovieCard.vue'

export default {
    components: {
        MovieCard
    },
}
</script>