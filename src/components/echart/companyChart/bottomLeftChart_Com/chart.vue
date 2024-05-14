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
              "亩均应税收入（万元）",
            ],
           textStyle: {
              color: "#B4B4B4",
              fontSize: 20,
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
            axisLabel: {
              textStyle: {
                fontSize: 16, 
              },
            },
          },
          yAxis: {
            type: "value",
            axisLabel: {
              textStyle: {
                fontSize: 16, 
              },
            },
          },
          series: [
            {
              name: "亩均应税收入（万元）",
              type: "line",
              stack: "Total",
              data: newData.total,
            }
          ],
        };
      },
      immediate: true,
      deep: true,
    },
  },
};
</script>
