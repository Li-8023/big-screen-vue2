<template>
  <div id="bottomLeft">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' style="font-size: 20px;"></i>
        </span>
        <div class="d-flex" >
          <span class="text mx-2" style="font-size: 20px;">应税收入情况</span>
          <dv-decoration-6 style="width:200px;height:20px;" />  
        </div>
      </div>
      <div>
        <BottomLeftChartCom />
      </div>
    </div>
  </div>
</template>

<script>
import BottomLeftChartCom from '@/components/echart/companyChart/bottomLeftChart_Com'
export default {
  components: {
    BottomLeftChartCom
  }
}
</script>

<style lang="scss" scoped>
$box-height: 520px;
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
  .chart-box {
    margin-top: 16px;
    width: 170px;
    height: 170px;
    .active-ring-name {
      padding-top: 10px;
    }
  }
}
</style>
