<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue';
export default {
  data () {
    return {
      cdata: {
        xData: ["data1", "data2", "data3", "data4"],
        seriesData: [
          { value: 30, name: "亩均应税收入" },
          
          { value: 15, name: "安全生产" },
          { value: 30, name: "亩均税收" },
          { value: 15, name: "环境保护" }
        ]
      }
    }
  },
  components: {
    Chart,
  },
  mounted () {
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
</style>