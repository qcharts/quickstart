<template>
  <div id="app" ref="app"></div>
</template>

<script>
import { Chart, Line, Legend, Tooltip, Axis } from '@qcharts/core'
const data = [
  { date: '05-01', catgory: '图例一', sales: 15.2 },
  { date: '05-02', catgory: '图例一', sales: 39.2 },
  { date: '05-03', catgory: '图例一', sales: 31.2 },
  { date: '05-04', catgory: '图例一', sales: 65.2 },
  { date: '05-05', catgory: '图例一', sales: 55.2 },
  { date: '05-06', catgory: '图例一', sales: 75.2 },
  { date: '05-07', catgory: '图例一', sales: 95.2 },
  { date: '05-08', catgory: '图例一', sales: 100 }
]
export default {
  name: 'app',
  components: {},
  mounted() {
    let $dom = this.$refs['app']
    const chart = new Chart({
      container: $dom
    })
    chart.source(data, {
      row: 'catgory',
      value: 'sales',
      text: 'date'
    })

    const line = new Line()
    line.style('point', { strokeColor: '#fff' })

    const tooltip = new Tooltip({
      formatter: function (data) {
        return `${data.date} ${data.sales}`
      }
    })

    const axisBottom = new Axis().style('grid', false)

    const axisLeft = new Axis({ orient: 'left' }).style('axis', false).style('scale', false)

    const legend = new Legend({ align: ['center', 'bottom'] }).style('icon', { borderRadius: 10 }).style('text', { fontSize: 12 })

    chart.append([line, tooltip, axisBottom, axisLeft, legend])
  }
}
</script>

<style>
#app {
  width: 600px;
  height: 400px;
}
</style>
