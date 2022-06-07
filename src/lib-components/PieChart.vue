<template>
  <base-chart :config="this.$props" :data="data" :type="type" />
</template>
<script>
import * as am4charts from '@amcharts/amcharts4/charts';
import BaseChart from './BaseChart.vue';

export default {
  components: { BaseChart },
  name: 'PieChart',
  props: {
    data: Array,
    series: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      type: am4charts.PieChart,
    };
  },
};
</script>
