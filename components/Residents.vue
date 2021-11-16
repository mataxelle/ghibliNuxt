<template>
    <v-card class="my-12">
        <v-card-title>name : {{ resident.name }}</v-card-title>
    </v-card>
</template>

<script>
export default {
    name: "Residents",

    props: {
        resident: {
            required: true
        }
    }
}
</script>