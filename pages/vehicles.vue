<template>
    <div>
        <h1 class="text-center my-6">All vehicles</h1>

        <div class="row my-6">
            <div class="col-lg-4 col-md-5 col-sm-5 mx-auto" v-for="vehicle in vehicles" :key="vehicle.id">
                <Vehicles :vehicle="vehicle" />
            </div>
        </div>
    </div>
</template>

<script>
import Vehicles from '@/components/Vehicles.vue'
import axios from 'axios'

export default {
    components: {
        Vehicles
    },

    async asyncData() {
        try {
            const apiVehicle = 'https://ghibliapi.herokuapp.com/vehicles'
            const vehicles = await axios.get(apiVehicle).then((response) => {
                return response.data
            })
            return { vehicles }

        } catch (error) {
            return { error }
        }
    }
}
</script>