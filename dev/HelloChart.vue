<script lang="ts">
import * as am4charts from '@amcharts/amcharts4/charts';
import Vue from 'vue';

am4charts.XYChart;

export default Vue.extend({
  name: 'ServeDev',
  data() {
    /* 랜덤 방문자수 */
    let data = [];
    let visits = 10;
    for (let i = 1; i < 366; i++) {
      visits += Math.round((Math.random() < 0.5 ? 1 : -1) * Math.random() * 10);
      data.push({
        date: new Date(2018, 0, i),
        name: 'name' + i,
        value: visits,
      });
    }
    return {
      data,
    };
  },
});
</script>

<template>
  <x-y-chart
    :data="data"
    :paddingRight="20"
    :scrollbarX="{
      type: 'XYChartScrollbar',
    }"
    :series="[
      {
        type: 'LineSeries',
        dataFields: { dateX: 'date', valueY: 'value' },
        tooltipText: '{valueY.value}',
      },
    ]"
    :xAxes="[{ type: 'DateAxis', 'renderer.grid.template.location': 0 }]"
    :yAxes="[
      {
        type: 'ValueAxis',
        renderer: { minWidth: 35 },
        tooltip: { disabled: true },
      },
    ]"
    class="hello"
    ref="xyChart"
  />
</template>

<style scoped>
.hello {
  min-height: 100vh;
}
</style>
