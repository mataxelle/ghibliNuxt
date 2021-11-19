<template>
    <div class="container">
    <div class="row">
      <div class="col-10 offset-1">
        <SpecieCard />
      </div>
    </div>
  </div>
</template>

<script>
import SpecieCard from '@/components/SpecieCard.vue'

export default {
    components: {
        SpecieCard
    },
}
</script>