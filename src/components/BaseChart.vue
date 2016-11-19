<template>
  <svg class="chart"></svg>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  props: ['chartData'],
  methods: {
    renderChart () {
      // Please override this method in subclasses.
    }
  },
  mounted () {
    this.renderChart()
  },
  watch: {
    chartData: 'renderChart'
  }
})
</script>

<style>
</style>
