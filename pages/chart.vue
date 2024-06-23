<template>
  <Highcharts :options="chartOptions" />
</template>

<script setup>
import { ref, onMounted } from 'vue'
// import { useHighcharts } from '@nuxtjs/highcharts'

// const { Highcharts } = useHighcharts()

const chartOptions = ref({
  chart: {
    type: 'line'
  },
  title: {
    text: 'COVID-19 Data'
  },
  xAxis: {
    categories: []
  },
  series: [
    {
      name: 'Cases',
      data: []
    }
  ]
})

onMounted(async () => {
  const response = await fetch('https://disease.sh/v3/covid-19/historical/all?lastdays=30')
  const data = await response.json()
console.log('data', data)
  chartOptions.value.xAxis.categories = Object.keys(data.cases)
  chartOptions.value.series[0].data = Object.values(data.cases)
})
</script>

<style scoped>
/* Gaya CSS khusus jika diperlukan */
</style>
