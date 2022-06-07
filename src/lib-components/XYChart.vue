<template>
  <base-chart :config="this.$props" :data="data" :type="type" />
</template>
<script>
import * as am4charts from '@amcharts/amcharts4/charts';
import BaseChart from './BaseChart.vue';

export default {
  components: { BaseChart },
  name: 'XYChart',
  props: {
    data: Array,
    scrollbarX: Object,
    scrollbarY: Object,
    series: {
      type: Array,
      required: true,
    },
    xAxes: Array,
    yAxes: Array,
  },
  data() {
    return {
      type: am4charts.XYChart,
    };
  },
};
</script>
