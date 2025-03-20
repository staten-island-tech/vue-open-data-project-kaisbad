<template>
  <div></div>
</template>

<script setup>
const chartData = computed(() => ({
  labels: covidlist.value.map((item) => item.date_of_interest),
  datasets: [
    {
      label: 'COVID Case Counts',
      backgroundColor: '#f87979',
      data: covidlist.value.map((item) => item.case_count),
    },
    {
      label: '7 Day Average',
      backgroundColor: '#7979F8', // A contrasting color
      data: covidlist.value.map((item) => item.case_count_7day_avg),
      borderColor: '#7979F8',
      fill: false,
    },
  ],
}))
</script>

<style scoped></style>
