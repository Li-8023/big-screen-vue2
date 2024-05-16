<template>
  <div>
    <!-- 年度开工率 -->
    <Echart
      :options="options"
      id="bottomLeftChart2"
      height="430px"
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
            backgroundColor: "#1f1f1f",
            axisPointer: {
              type: "shadow",
              label: {
                show: true,
                backgroundColor: "#7B7DDC",
              },
            },
          },
          legend: {
            textStyle: {
              fontSize: 16,
            },
          },
          grid: {
            left: "3%",
            right: "4%",
            bottom: "3%",
            containLabel: true,
          },
          xAxis: [
            {
              type: "category",
              data: newData.category,
              axisLine: {
                lineStyle: {
                  color: "#B4B4B4",
                },
              },
              axisTick: {
                show: false,
              },
              axisLabel: {
                textStyle: {
                  fontSize: 16,
                },
              },
            },
          ],
          yAxis: [
            {
              type: "value",
              axisLabel: {
                textStyle: {
                  fontSize: 16,
                },
              },
              splitLine: {
                show: false,
              },
              axisLine: {
                lineStyle: {
                  color: "#B4B4B4",
                },
              },
            },
            {
              splitLine: { show: false },
              axisLine: {
                lineStyle: {
                  color: "#B4B4B4",
                },
              },
              axisLabel: {
                formatter: "{value} ",
              },
            },
          ],
          series: [
            {
              name: "总应税收入一季度",
              type: "bar",
              stack: "Ad",
              barWidth: 40,
              emphasis: {
                focus: "series",
              },
              itemStyle: {
                normal: {
                  color: "#b91a07",
                },
              },
              data: newData.tax_one,
            },
            {
              name: "总应税收入二季度",
              type: "bar",
              stack: "Ad",
              barWidth: 40,
              emphasis: {
                focus: "series",
              },
              itemStyle: {
                normal: {
                  color: "#e7461c",
                },
              },
              data: newData.tax_two,
            },
            {
              name: "总应税收入三季度",
              type: "bar",
              stack: "Ad",
              barWidth: 40,
              emphasis: {
                focus: "series",
              },
              itemStyle: {
                normal: {
                  color: "#e77a5b",
                },
              },
              data: newData.tax_three,
            },
            {
              name: "总应税收入四季度",
              type: "bar",
              stack: "Ad",
              barWidth: 40,
              emphasis: {
                focus: "series",
              },
              itemStyle: {
                normal: {
                  color: "#f6ab98",
                },
              },
              data: newData.tax_four,
            },

            {
              name: "同比增长速度",
              type: "line",
              showAllSymbol: true,
              symbol: "emptyCircle",
              symbolSize: 8,
              smooth: false,
              yAxisIndex: 1,
              emphasis: {
                focus: "series",
              },
              itemStyle: {
                normal: {
                  color: "#cccccc",
                },
              },
              data: newData.tax_rate,
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
