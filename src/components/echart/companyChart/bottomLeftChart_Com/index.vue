<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from "./chart.vue";
export default {
  data() {
    return {
      cdata: {
        category: [
          "2019年报",
          "2020年报",
          "2021年报",
          "2022年报",
          "2023年报",
          "2024年报",
        ],
        lineData: [120, 240, 360, 480, 600, 720],
        rateData: [180, 300, 420, 540, 660, 780],
        barData: [240, 360, 480, 600, 720, 840],
        forthData: [300, 420, 540, 660, 780, 900],
        lineChartData: [20, 25, 28, 31, 33, 35],
      },
    };
  },
  components: {
    Chart,
  },
  mounted() {
    this.setData();
  },
};
</script>

<style lang="scss" scoped></style>
