<template>
  <div id="centerRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' style="font-size: 20px;"  ></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2" style="font-size: 20px;">企业情况</span>  
          <dv-decoration-1 style="width:200px;height:20px;" />    
        </div>
      </div>
      <div>
        <BottomRightChart />
      </div>
    </div>
  </div>
</template>

<script>
import BottomRightChart from '@/components/echart/companyChart/bottomRightChart'
export default {
  
 components:{
  BottomRightChart,
 }
}
</script>

<style lang="scss" scoped>
$box-height: 520px;
$box-width: 100%;
#centerRight1 {
  padding: 16px;
  padding-top: 20px;
  height: $box-height;
  width: $box-width;
  border-radius: 5px;
  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .body-box {
    border-radius: 10px;
    overflow: hidden;
    .dv-scr-board {
      width: 650px;
      height: 340px;
    }
  }
  .d-flex{
    margin-bottom: 10px;
  }
}
</style>
