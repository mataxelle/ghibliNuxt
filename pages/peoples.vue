<template>
    <div>
        <h1 class="text-center my-6">All Peoples</h1>
        <v-row>
            <v-col v-for="people in peoples" :key="people.id">
                <Peoples :people="people" />
            </v-col>
        </v-row>
    </div>
</template>

<script>
import Peoples from '@/components/Peoples.vue'
import axios from 'axios'

export default {
    components: {
        Peoples
    },

    /*data() {
        return {
            peoples: []
        }
    },
    No need data() when using async hook
    */

    async asyncData() {
        try {
            const apiPeople = 'https://ghibliapi.herokuapp.com/people'
            const peoples = await axios.get(apiPeople).then((response) => {
                return response.data
            })
            return { peoples }

        } catch (error) {
            return { error }
        }
    }
}
</script>