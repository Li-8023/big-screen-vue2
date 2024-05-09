<template>
  <div>
    <Echart
      :options="options"
      id="bottomLeftChartCom"
      height="480px"
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
              "企业所得税（万元）",
              "消费税（万元）",
              "增值税（万元）",
              "营业税（万元）",
              "个人所得税（万元）",
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
              name: "企业所得税（万元）",
              type: "line",
              stack: "Total",
              data: newData.total,
            },
            {
              name: "消费税（万元）",
              type: "line",
              stack: "Total",
              data: newData.consume,
            },
            {
              name: "增值税（万元）",
              type: "line",
              stack: "Total",
              data: newData.added,
            },
            {
              name: "营业税（万元）",
              type: "line",
              stack: "Total",
              data: newData.business,
            },
            {
              name: "个人所得税（万元）",
              type: "line",
              stack: "Total",
              data: newData.personal,
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
