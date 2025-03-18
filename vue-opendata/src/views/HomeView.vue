<script setup>
import { ref, onMounted, computed } from 'vue'
import CovidChart from '@/components/CovidChart.vue'

const covidlist = ref([])
async function covidData() {
  try {
    let results = await fetch('https://data.cityofnewyork.us/resource/rc75-m7u3.json')
    let data = await results.json()
    covidlist.value = data
    console.log(data)
  } catch (error) {
    console.error('Error fetching COVID data:', error)
  }
}

onMounted(() => {
  covidData()
})

const chartData = computed(() => {
  return {
    labels: covidlist.value.map((item) => item.date_of_interest),
    datasets: [
      {
        label: 'COVID Case Counts',
        backgroundColor: '#f87979',
        data: covidlist.value.map((item) => item.case_count),
      },
    ],
  }
})
</script>

<template>
  <main>
    <h1 class="text-4xl">COVID Case Counts</h1>
    <div class="h-450px" v-if="covidlist.length">
      <CovidChart :chartData="chartData" />
    </div>
  </main>
</template>
<!-- <template>
  <main>
    <h1>COVID Case Counts</h1>
    <div v-if="covidlist.length">
      <p v-for="(cdata, index) in covidlist" :key="index">
        {{ cdata.case_count }}
      </p>
    </div>
    <p v-else>Loading data...</p>
  </main>
</template>
 -->
