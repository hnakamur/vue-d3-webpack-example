<template>
  <div id="app">
    <chart v-bind:chart-data="chartData"></chart>
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
      chartData: [4, 8, 15, 16, 23, 42]
    }
  }
}
</script>

<style>
</style>
