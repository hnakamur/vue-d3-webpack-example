<template>
  <div id="app">
    <bar-chart :chart-data="barChart.data" :width="barChart.width" :bar-height="barChart.barHeight"></bar-chart>
    <line-chart :chart-data="lineChart.data" :width="lineChart.width" :height="lineChart.height"></line-chart>
  </div>
</template>

<script>
import BarChart from './components/BarChart'
import LineChart from './components/LineChart'

export default {
  name: 'app',
  components: {
    BarChart,
    LineChart
  },
  data () {
    return {
      barChart: {
        data: [4, 8, 15, 16, 23, 42],
        width: 420,
        barHeight: 20
      },
      lineChart: {
        data: [
          { date: '1-May-12', close: 58.13 },
          { date: '30-Apr-12', close: 53.98 },
          { date: '27-Apr-12', close: 67.00 },
          { date: '26-Apr-12', close: 89.70 },
          { date: '25-Apr-12', close: 99.00 },
          { date: '24-Apr-12', close: 130.28 },
          { date: '23-Apr-12', close: 166.70 },
          { date: '20-Apr-12', close: 234.98 },
          { date: '19-Apr-12', close: 345.44 },
          { date: '18-Apr-12', close: 443.34 },
          { date: '17-Apr-12', close: 543.70 },
          { date: '16-Apr-12', close: 580.13 },
          { date: '13-Apr-12', close: 605.23 },
          { date: '12-Apr-12', close: 622.77 },
          { date: '11-Apr-12', close: 626.20 },
          { date: '10-Apr-12', close: 628.44 },
          { date: '9-Apr-12', close: 636.23 },
          { date: '5-Apr-12', close: 633.68 },
          { date: '4-Apr-12', close: 624.31 },
          { date: '3-Apr-12', close: 629.32 },
          { date: '2-Apr-12', close: 618.63 },
          { date: '30-Mar-12', close: 599.55 },
          { date: '29-Mar-12', close: 609.86 },
          { date: '28-Mar-12', close: 617.62 },
          { date: '27-Mar-12', close: 614.48 },
          { date: '26-Mar-12', close: 606.98 }
        ],
        width: 800,
        height: 600
      }
    }
  }
}
</script>
