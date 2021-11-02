<template>
    <div>
        <h1 class="text-center my-6">Tous les films</h1>

        <Movie />
    </div>
</template>

<script>
import Movie from '@/components/Movie.vue'

export default {
    components: {
        Movie
    }
    
}
</script>