<template>
  <div>
    <Echart
      :options="options"
      id="topRightCom"
      height="320px"
      width="100%"
    ></Echart>
  </div>
</template>
<script>
import Echart from "@/common/echart";
export default {
  data() {
    return {
      options: {},
    };
  },
  components: {
    Echart,
  },
  props: {
    cdata: {
      type: Object,
      default: () => ({}),
    },
  },
  watch: {
    cdata: {
      handler(newData) {
        this.options = {
          tooltip: {
            trigger: "axis",
            backgroundColor: "rgba(255,255,255,0.1)",
            axisPointer: {
              type: "shadow",
              label: {
                show: true,
                backgroundColor: "#7B7DDC",
              },
            },
          },
          legend: {
            data: [
              "用电量",
              "能耗",
              "环保得分",
              "安全得分",
            ],
            textStyle: {
              color: "#B4B4B4",
            },
            top: "0%",
          },
          grid: {
            left: "3%",
            right: "4%",
            bottom: "3%",
            containLabel: true,
          },
          xAxis: {
            type: "category",
            boundaryGap: false,
            data: newData.category,
          },
          yAxis: {
            type: "value",
          },
          series: [
            {
              name: "用电量",
              type: "line",
              stack: "Total",
              data: newData.electric,
            },
            {
              name: "能耗",
              type: "line",
              stack: "Total",
              data: newData.energy,
            },
            {
              name: "环保得分",
              type: "line",
              stack: "Total",
              data: newData.env,
            },
            {
              name: "安全得分",
              type: "line",
              stack: "Total",
              data: newData.safe,
            },
          ],
        };
      },
      immediate: true,
      deep: true,
    },
  },
};
</script>
