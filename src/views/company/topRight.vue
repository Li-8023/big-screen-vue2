<template>
  <div id="envRanking">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' ></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2">经营情况</span>
          <dv-decoration-6 style="width:200px;height:20px;" />  
        </div>
      </div>
      <!-- <div class="d-flex jc-center body-box">
        <dv-scroll-board class="dv-scr-board" :config="config" />
      </div> -->
      <div>
        <TopRight />
      </div>
    </div>
  </div>
</template>

<script>
import TopRight from '@/components/echart/companyChart/topRight';

export default {
  components: {
    TopRight
  }
}
</script>

<style lang="scss" scoped>
$box-height: 410px;
$box-width: 800px;
#envRanking {
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
