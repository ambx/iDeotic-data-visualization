<template>

  <h1>Diesel Prices in Bengaluru from 2011 to 2020</h1>
  <LineChart v-if="chartData" :chartData="chartData" />
  <br />

</template>

<script>
import { defineComponent, onMounted, ref } from "@vue/runtime-core";
import dieselData from "../assets/diesel.csv?raw";
import Papa from "papaparse";
import { LineChart } from "vue-chart-3";
import { Chart, registerables } from "chart.js";
Chart.register(...registerables);



export default defineComponent({          
  components: { LineChart },
  setup() {
    const chartData = ref();
    

    const processCSVFIle = () => {
      const { data } = Papa.parse(dieselData, {
        header: true,
        dynamicTyping: true,
      });
      
      const bengaluruData = data.filter((item) => item.city === "Bengaluru");
      const formattedData = bengaluruData.reduce(
        (result, item) => {
          return {
            label: [...result.label, item.date],
            data: [...result.data, item.rate],
          };
        },
        {
          label: [],
          data: [],
        }
      );

      chartData.value = {
        labels: formattedData.label,
        datasets: [
          {
            label: "Bengaluru",
            data: formattedData.data,
            fill: false,
            borderColor: "rgb(255, 99, 132)",
            tension: 0.1,
            pointBorderColor: "rgba(0, 0, 0, 0)",
            pointBackgroundColor: "rgba(0,0,0,0)",
          },
        ],
      };
    };

    onMounted(() => {
      processCSVFIle();
    });

    return { chartData };
  },
}
);

</script>

<style>
@import "../assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>
