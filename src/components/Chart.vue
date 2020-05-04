<template>
  <div>
    <div id="chart" ref="barchart"></div>
  </div>
</template>>

<script>
import ApexCharts from 'apexcharts'

export default {
  methods: {
    renderChart (dataTime, dataTemp) {
      new ApexCharts(this.$refs.barchart, {
        chart: {
          type: 'bar',
          height: 400
        },
        series: [{
          name: 'sales',
          data: dataTemp
        }],
        xaxis: {
          categories: dataTime
        }
      }).render()
    }
  }
}
</script>>