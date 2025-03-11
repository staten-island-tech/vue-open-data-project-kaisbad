<template>
  <div>
    <canvas ref="chart"></canvas>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import { Chart, registerables } from 'chart.js'
import { Bar } from 'vue-chartjs'

Chart.register(...registerables)

const props = defineProps({
  chartData: {
    type: Object,
    required: true,
  },
})

const chart = ref(null)

onMounted(() => {
  renderChart()
})

watch(
  () => props.chartData,
  () => {
    renderChart()
  },
)

function renderChart() {
  if (chart.value) {
    new Chart(chart.value, {
      type: 'bar',
      data: props.chartData,
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          y: {
            beginAtZero: true,
          },
        },
      },
    })
  }
}
</script>
