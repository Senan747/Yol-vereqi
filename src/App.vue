<script setup>
import Main from "./components/Main.vue";
import Chart from "./components/Chart.vue";
import Map from "./components/Map.vue";
</script>

<template>
  <div class="total">
    <Main />
    <Chart />
  </div>
  <Map />
</template>

<style scoped>
.total {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 50px;
}
</style>
