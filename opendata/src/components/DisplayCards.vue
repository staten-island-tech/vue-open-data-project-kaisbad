<template>
  <div class="text-center">
    <h2 class="text-xl font-bold mt-1">{{ chartCard.date_of_interest }}</h2>
    <p class="text-l">Event: {{ chartCard.case_count }}</p>
    <p class="text-l">Price: ${{ chartCard.death_count }}</p>
  </div>
</template>

<script setup>
const props = defineProps({
  chartCard: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped></style>
