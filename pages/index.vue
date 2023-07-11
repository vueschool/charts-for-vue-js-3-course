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

type movie = { title: string; rating: number };
const movies = ref<movie[]>([]);
fetch("/api.json")
  .then(async (res) => (movies.value = await res.json()))
  .catch((error) => alert(error.message));
const chartData = computed((): ChartData<"bar"> => {
  return {
    labels: movies.value.map((movie) => movie.title),
    datasets: [
      {
        backgroundColor: ["#c82834", "#244771"],
        data: movies.value.map((movie) => movie.rating),
      },
    ],
  };
});
</script>
<template>
  <Bar
    v-if="movies.length"
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
