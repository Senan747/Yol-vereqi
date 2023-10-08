<script setup>
import Main from "./components/LineChart.vue";
import Chart from "./components/BarChart.vue";
import Map from "./components/Map.vue";
</script>

<template>
  <div class="total">
    <div class="charts">
      <Main />
      <Chart />
    </div>
    <Map />
  </div>
</template>

<style scoped>
.total {
  margin: 50px;
}
.charts {
  display: flex;
  flex-direction: row;
  align-items: center;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-bottom: 50px;
}
</style>
