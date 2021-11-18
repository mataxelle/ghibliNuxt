<template>
    <div>
        <h1 class="text-center my-6">All species</h1>
        <div class="row my-6">
            <div class="col-lg-4 col-sm-5 mx-auto" v-for="specie in species" :key="specie.id">
                <Species :specie="specie" />
            </div>
        </div>
    </div>
</template>

<script>
import Species from '@/components/Species.vue'
import axios from 'axios'

export default {
    components: {
        Species
    },

    async asyncData() {
        try {
            const apiSpecies = 'https://ghibliapi.herokuapp.com/species'
            const species = await axios.get(apiSpecies).then((response) => {
                return response.data
            })
            return { species }

        } catch (error) {
            return { error }
        }
    }
}
</script>