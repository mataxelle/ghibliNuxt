<template>
    <div class="container">
    <div class="row">
      <div class="col-10 offset-1">
        <PeopleCard />
      </div>
    </div>
  </div>
</template>

<script>
import PeopleCard from '@/components/PeopleCard.vue'

export default {
    components: {
        PeopleCard
    },
}
</script>