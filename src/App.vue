<template>
  <div id="app">
    <chart :chart-data="chartData" :width="chartWidth" :bar-height="barHeight"></chart>
  </div>
</template>

<script>
import Chart from './components/Chart'

export default {
  name: 'app',
  components: {
    Chart
  },
  data () {
    return {
      chartData: [4, 8, 15, 16, 23, 42],
      chartWidth: 420,
      barHeight: 20
    }
  }
}
</script>
