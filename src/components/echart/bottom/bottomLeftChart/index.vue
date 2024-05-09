<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue'
export default {
  data () {
    return {
      cdata: {
        category: [
          "一月",
          "二月",
          "三月",
          "四月",
          "五月",
          "六月",
          "七月",
          "八月",
          "九月",
          "十月",
          "十一月",
          "十二月",

          // "市区",
          // "万州",
          // "江北",
          // "南岸",
          // "北碚",
          // "綦南",
          // "长寿",
          // "永川",
          // "璧山",
          // "江津",
          // "城口",
          // "大足",
          // "垫江",
          // "丰都",
          // "奉节",
          // "合川",
          // "江津区",
          // "开州",
          // "南川",
          // "彭水",
          // "黔江",
          // "石柱",
          // "铜梁",
          // "潼南",
          // "巫山",
          // "巫溪",
          // "武隆",
          // "秀山",
          // "酉阳",
          // "云阳",
          // "忠县",
          // "川东",
          // "检修"
        ],
        //亩均
        lineData: [
          59,
          34,
          40,
          50,
          60,
          56,
          35,
          28,
          57,
          46,
          59,
          60
        ],
        //环境与安全
        barData: [
          30,
          29,
          28,
          24,
          30,
          18,
          28,
          24,
          23,
          26,
          30,
          26
        ],
        //总得分
        rateData: [
          30,
          50,
          60,
          40,
          30,
          60,
          70,
          90,
          90,
          70,
          90,
          100
        ]
      }
    };
  },
  components: {
    Chart,
  },
  mounted () {
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
  }
};
</script>

<style lang="scss" scoped>
</style>