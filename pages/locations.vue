<template>
    <div>
        <h1 class="text-center my-6">All locations</h1>

        <div class="row my-6">
            <div class="col-lg-4 col-md-5 col-sm-5 mx-auto" v-for="location in locations" :key="location.id">
                <Locations :location="location" />
            </div>
        </div>
    </div>
</template>

<script>
import Locations from '@/components/Locations.vue'
import axios from 'axios'

export default {
    components: {
        Locations
    },

    async asyncData() {
        try {
            const apiLocation = 'https://ghibliapi.herokuapp.com/locations'
            const locations = await axios.get(apiLocation).then((response) => {
                return response.data
            })
            return { locations }

        } catch (error) {
            return { error }
        }
    }
}
</script>