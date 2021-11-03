<template>
    <div>
        <h1 class="text-center my-6">Tous les films</h1>

        <Movies />
    </div>
</template>

<script>
import Movies from '@/components/Movies.vue'

export default {
    components: {
        Movies
    }
    
}
</script>