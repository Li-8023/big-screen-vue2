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
        lineData: [700, 600, 500, 400, 300, 200],
        rateData: [680, 580, 480, 380, 280, 180],
        barData: [660, 560, 460, 360, 260, 160],
        forthData: [640, 540, 440, 340, 240, 140],
        lineChartData: [-2.86, -3.33, -4.17, -5, -6.67, -7.14],
      },
    };
  },
  components: {
    Chart,
  },
  mounted() {
    this.setData();
  },
  methods: {
    // 根据自己的业务情况修改
    // setData () {
    //   for (let i = 0; i < this.cdata.barData.length -1; i++) {
    //     let rate = this.cdata.barData[i] / this.cdata.lineData[i];
    //     this.cdata.rateData.push(rate.toFixed(2));
    //   }
    // },
  },
};
</script>

<style lang="scss" scoped></style>
