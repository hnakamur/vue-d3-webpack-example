<template>
  <div id="app">
    <bar-chart :chart-data="barChart.data" :width="barChart.width" :bar-height="barChart.barHeight"></bar-chart>
  </div>
</template>

<script>
import BarChart from './components/BarChart'

export default {
  name: 'app',
  components: {
    BarChart
  },
  data () {
    return {
      barChart: {
        data: [4, 8, 15, 16, 23, 42],
        width: 420,
        barHeight: 20
      }
    }
  }
}
</script>
