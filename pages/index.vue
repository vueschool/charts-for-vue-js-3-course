<script setup lang="ts">
import { Bar } from "vue-chartjs";
import type { ChartData } from "chart.js";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);
const chartData = ref<ChartData<"bar">>({
  labels: [
    "Spider-Man (2002)",
    "Spider-Man 2 (2004)",
    "Spider-Man 3 (2007)",
    "The Amazing Spider-Man (2012)",
    "The Amazing Spider-Man 2 (2014)",
    "Spider-Man: Homecoming (2017)",
    "Spider-Man: Far From Home (2019)",
    "Spider-Man: No Way Home (2021)",
    "Spider-Man: Into the Spider-Verse (2018)",
    "Spider-Man: Across the Spider-Verse (2023)",
  ],
  datasets: [
    {
      backgroundColor: ["#c82834", "#244771"],
      data: [7.3, 7.3, 6.2, 6.9, 6.6, 7.4, 7.5, 8.0, 8.4, 8.9],
    },
  ],
});
</script>
<template>
  <Bar
    :data="chartData"
    :options="{
      plugins: {
        legend: { display: false },
      },
    }"
  />
</template>
<style>
body {
  padding: 50px;
}
</style>
