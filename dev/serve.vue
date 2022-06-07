<script lang="ts">
import Vue from 'vue';
import HelloChart from './HelloChart.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    HelloChart,
  },
});
</script>

<template>
  <div id="app">
    <hello-chart />
  </div>
</template>
