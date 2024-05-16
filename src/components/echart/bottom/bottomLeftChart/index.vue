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
        lineData: [100, 200, 300, 400, 500, 700],
        rateData: [150, 250, 350, 450, 460, 480],
        barData: [200, 300, 400, 500, 600, 750],
        forthData: [250, 350, 450, 550, 600, 700],
        lineChartData: [400, 250, 166.67, 125, -8, 4.35],

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
