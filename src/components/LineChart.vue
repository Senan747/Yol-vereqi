<template>
  <div class="card-body">
    <div>
      <select v-model="selectedYear">
        <option value="2021">2021</option>
        <option value="2022">2022</option>
        <option value="2023">2023</option>
      </select>
    </div>
    <div id="chart" class="chart-lg"></div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";
import ApexCharts from "apexcharts";
import data from "../../db.json";

const chart = ref(null);
const selectedYear = ref("2021");

onMounted(() => {
  createChart(selectedYear.value);
});

watch(selectedYear, (newYear) => {
  createChart(newYear);
});

function createChart(year) {
  const options = {
    chart: {
      type: "line",
    },
    series: data.map((item) => ({
      name: item.car,
      data: item.year[year].fuelMonthly,
    })),
    xaxis: {
      categories: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ],
    },
  };
  
  if (chart.value) {
    chart.value.destroy();
  }

  chart.value = new ApexCharts(document.querySelector("#chart"), options);
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

#chart {
  min-width: 650px;
}
</style>
