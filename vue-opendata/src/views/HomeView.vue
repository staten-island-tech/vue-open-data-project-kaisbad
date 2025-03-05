<script setup>
import { ref, onMounted } from 'vue'
const covidlist = ref('')
async function covidData() {
  let results = await fetch('https://data.cityofnewyork.us/resource/rc75-m7u3.json')
  let data = await results.json()
  covidlist.value = data.results
}
onMounted(() => {
  covidData()
})
</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template>
