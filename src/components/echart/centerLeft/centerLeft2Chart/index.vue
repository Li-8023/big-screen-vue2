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
      cdata: [
        {
          // 名字需要与 “common/map/fujian.js” 地图数据文件里面定义的一一对应，不能是 “福州” 或者 “闽” 之类的缩写
          name: '福州市',
          value: 10,
          elseData:{
            // 这里放置地图 tooltip 里想显示的数据
          }
        },
        {
          name: 'XX区',
          value: 9,
        },
        {
          name: 'XX区',
          value: 8,
        },
        {
          name: 'XX区',
          value: 7,
        },
        {
          name: 'XX区',
          value: 6,
        },
        {
          name: 'XX区',
          value: 5,
        },
        {
          name: 'XX区',
          value: 4,
        },
        {
          name: 'XX区',
          value: 3,
        },
        {
          name: 'XX区',
          value: 2,
        }
      ]
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