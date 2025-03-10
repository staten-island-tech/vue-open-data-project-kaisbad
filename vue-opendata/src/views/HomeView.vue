<script setup>
import { ref, onMounted } from 'vue'
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
</script>

<template>
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
