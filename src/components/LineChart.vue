<template>
  <svg class="line-chart"></svg>
</template>

<script>
import BaseChart from './BaseChart'
import * as d3 from 'd3'

export default BaseChart.extend({
  name: 'line-chart',
  props: ['width', 'height'],
  methods: {
    renderChart () {
      // NOTE: This code is based on https://gist.github.com/d3noob/402dd382a51a4f6eea487f9a35566de0

      var data = this.chartData
      var margin = {
        top: 20,
        right: 20,
        bottom: 30,
        left: 50
      }
      var width = this.width - margin.left - margin.right
      var height = this.height - margin.top - margin.bottom

      var parseTime = d3.timeParse('%d-%b-%y')

      var x = d3.scaleTime()
        .range([0, width])
        .domain(d3.extent(data, (d) => parseTime(d.date)))

      var y = d3.scaleLinear()
        .range([height, 0])
        .domain([0, d3.max(data, (d) => d.close)])

      var valueline = d3.line()
        .x((d) => x(parseTime(d.date)))
        .y((d) => y(d.close))

      var svg = d3.select(this.$el)
        .attr('width', this.width)
        .attr('height', this.height)
        .append('g')
        .attr('transform', 'translate(' + margin.left + ',' + margin.top + ')')

      var d = svg.selectAll('path')
        .data([data])

      d.enter().append('path')
        .merge(d)
        .attr('class', 'line')
        .attr('d', valueline)

      svg.append('g')
        .attr('transform', 'translate(0,' + height + ')')
        .call(d3.axisBottom(x))

      svg.append('g')
        .call(d3.axisLeft(y))
    }
  },
  watch: {
    width: 'renderChart',
    height: 'renderChart'
  }
})
</script>

<style lang="scss">
.line-chart {
  .line {
    fill: none;
    stroke: steelblue;
    stroke-width: 2px;
  }
}
</style>
