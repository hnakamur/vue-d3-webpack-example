<template>
  <svg class="chart"></svg>
</template>

<script>
import * as d3 from 'd3'

export default {
  name: 'chart',
  props: ['chartData'],
  methods: {
    renderChart: function (data) {
      // This code is based on https://bost.ocks.org/mike/bar/2/

      var width = 420
      var barHeight = 20

      var x = d3.scaleLinear()
          .domain([0, d3.max(data)])
          .range([0, width])

      var chart = d3.select(this.$el)
          .attr('width', width)
          .attr('height', barHeight * data.length)

      var d = chart.selectAll('g')
          .data(data)

      d.exit().remove()

      var g = d.enter().append('g')
          .merge(d)
          .attr('transform', function (d, i) { return 'translate(0,' + i * barHeight + ')' })
      g.selectAll('rect').remove()
      g.selectAll('text').remove()
      g.append('rect')
          .attr('width', x)
          .attr('height', barHeight - 1)
      g.append('text')
          .attr('x', function (d) { return x(d) - 3 })
          .attr('y', barHeight / 2)
          .attr('dy', '.35em')
          .text(function (d) { return d })
    }
  },
  mounted: function () {
    this.renderChart(this.chartData)
  },
  watch: {
    chartData: function (val) {
      this.renderChart(val)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.chart rect {
  fill: steelblue;
}

.chart text {
  fill: white;
  font: 10px sans-serif;
  text-anchor: end;
}
</style>
