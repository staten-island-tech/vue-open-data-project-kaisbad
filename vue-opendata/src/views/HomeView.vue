<script setup>
import { ref, onMounted } from 'vue'
const covidlist = ref('')
async function covidData() {
  let results = await fetch('https://data.cityofnewyork.us/resource/rc75-m7u3.json')
  let data = await results.json()
  covidlist.value = data
}
onMounted(() => {
  covidData()
})
</script>

<template>
  <main>
    <h1>{{ covidlist.case_count }}</h1>
  </main>
</template>
