<template>
  <div>
    <Echart
      :options="options"
      id="bottomCenterChartCom"
      height="390px"
      width="100%"
    ></Echart>
  </div>
</template>

<script>
import Echart from "@/common/echart";
export default {
    data(){
        return {
            options:{},
        };
    },
    components: {
    Echart,
  },
    props:{
        cdata: {
            type: Object,
            default: () => ({}),
        },
    },
    watch:{
        cdata:{
            handler(newData){
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
                    xAxis: {
                        data: newData.category,
                        axisLabel: {
                        inside: true,
                        color: '#fff'
                        },
                        axisTick: {
                        show: false
                        },
                        axisLine: {
                        show: false
                        },
                        z: 10
                    },
                    yAxis: {
                        name:"单位：万元",
                        axisLine: {
                        show: false
                        },
                        axisTick: {
                        show: false
                        },
                        axisLabel: {
                        color: '#999'
                        }
                    },
                    series: [
                        {
                        type: 'bar',
                        showBackground: true,
                        itemStyle: {
                            color: '#188df0' 
                            // color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            // { offset: 0, color: '#83bff6' },
                            // { offset: 0.5, color: '#188df0' },
                            // { offset: 1, color: '#188df0' }
                            // ])
                        },
                        emphasis: {
                            itemStyle: {
                                 color: '#188df0' 
                            // color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            //     { offset: 0, color: '#2378f7' },
                            //     { offset: 0.7, color: '#2378f7' },
                            //     { offset: 1, color: '#83bff6' }
                            // ])
                            }
                        },
                        data: newData.num
                        },
                    ],
                };
            },
            immediate: true,
            deep: true,
        }
    }
}
</script>

<style></style>
