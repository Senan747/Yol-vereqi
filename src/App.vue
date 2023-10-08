<script setup>
import Main from "./components/Main.vue";
import Chart from "./components/Chart.vue";
</script>

<template>
  <div class="total">
    <Main />
    <Chart />
  </div>
</template>

<style scoped>
.total{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
</style>
