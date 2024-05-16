<template>
  <div id="bottomLeft">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class="bx bx-line-chart" style="font-size: 20px"></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2" style="font-size: 20px">数据统计图</span>
        </div>
      </div>
      <div class="chart-container">
        <button v-if="!modalActive" @click="prevChart" class="toggle-chart-btn left-btn">
          <i class="bx bxs-chevrons-left" style="color: #ffff; font-size: 40px;"></i>
        </button>
        <div class="chart-content">
          <BottomLeftChart v-if="currentChart === 0" />
          <BottomLeftChart2 v-else-if="currentChart === 1" />
          <BottomLeftChart3 v-else />
        </div>
        <button v-if="!modalActive" @click="nextChart" class="toggle-chart-btn right-btn">
          <i class="bx bxs-chevrons-right" style="color: #ffff; font-size: 40px;"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import BottomLeftChart from "@/components/echart/bottom/bottomLeftChart";
import BottomLeftChart2 from "@/components/echart/bottom/bottomLeftChart_2";
import BottomLeftChart3 from "@/components/echart/bottom/bottomLeftChart_3";

export default {
  props:{
    modalActive:{
      type: Boolean,
      default: false,
    }
  },
  components: {
    BottomLeftChart,
    BottomLeftChart2,
    BottomLeftChart3
  },
  data() {
    return {
      currentChart: 0 // State to manage which chart is currently displayed
    };
  },
  methods: {
    nextChart() {
      this.currentChart = (this.currentChart + 1) % 3; // Cycle through 0, 1, 2
    },
    prevChart() {
      this.currentChart = (this.currentChart + 2) % 3; // Cycle backwards through 0, 1, 2
    }
  }
};
</script>

<style lang="scss" scoped>
$box-height: 500px;
$box-width: 100%;
#bottomLeft {
  padding: 20px 16px;
  height: $box-height;
  width: $box-width;
  border-radius: 5px;
  .bg-color-black {
    height: $box-height - 35px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .chart-container {
    position: relative;
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .chart-content {
    margin-left: 10px;
    width: 100%;
    height: calc(100% - 40px); // Adjust height based on container
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .chart-content > div {
    width: 100%;
    height: 100%;
  }
  .toggle-chart-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: none;
    border: none;
    cursor: pointer;
    z-index: 1;
  }
  .toggle-chart-btn.left-btn {
    left: 0;
  }
  .toggle-chart-btn.right-btn {
    right: 0;
  }
}
</style>
