<template>
  <div class="card-body">
    <div>
      <select v-model="selectedYear">
        <option value="2021">2021</option>
        <option value="2022">2022</option>
        <option value="2023">2023</option>
      </select>
    </div>
    <div id="chart-bar" class="chart-lg"></div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";
import ApexCharts from "apexcharts";
import data from "../../db.json";

const selectedYear = ref("2021");
const chart = ref(null);
onMounted(() => {
  createBarChart(selectedYear.value);
});

watch(selectedYear, (newYear) => {
  createBarChart(newYear);
});

function createBarChart(year) {
  const series = data.map((item) => ({
    name: item.car,
    data: item.year[year].visitedCount,
  }));

  const options = {
    chart: {
      type: "bar",
    },
    series: series,
    xaxis: {
      categories: ["Baku", "Ganja", "Lankaran", "Sheki"],
    },
  };

  if (chart.value) {
    chart.value.destroy();
  }

  chart.value = new ApexCharts(document.querySelector("#chart-bar"), options);
  chart.value.render();
}
</script>

<style scoped>
select {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 200px;
}

option {
  font-size: 14px;
  background-color: #fff;
}
.card-body {
  max-width: 100vw;
  height: auto;
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: center;
}
#chart-bar {
  min-width: 650px;
}
</style>
