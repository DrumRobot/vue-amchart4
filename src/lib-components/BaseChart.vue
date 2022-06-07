<template>
  <div id="chartdiv"></div>
</template>
<script lang="ts">
import { Chart } from '@amcharts/amcharts4/charts';
import * as am4core from '@amcharts/amcharts4/core';
import Vue from 'vue';
import Component from 'vue-class-component';

const BaseProps = Vue.extend({
  name: 'BaseChart',
  props: {
    data: Array,
    type: Function,
    config: Object,
  },
  watch: {
    data(data: any[]) {
      (this as BaseChart).$chart!.data = data;
    },
  },
});

@Component
class BaseChart extends BaseProps {
  $chart?: Chart;

  mounted() {
    let { config, type, ...props } = this.$props;
    config = { ...config, ...props };
    this.$chart = am4core.createFromConfig(config, 'chartdiv', type) as Chart;
  }

  beforeDestroy() {
    this.$chart?.dispose();
  }
}
export default BaseChart;
</script>
