<template>
  <div id="safeRanking">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <!-- <icon name="chart-line" class="text-icon"></icon> -->
          <i class='bx bx-line-chart'></i>
        </span>
        <div class="d-flex">
          <span class=" text mx-2">安全生产排行榜</span>
          <!-- <span class="fs-xl text mx-2">企业得分排行榜</span> -->
          
        </div>
      </div>
      <div class="d-flex jc-center body-box">
        <dv-scroll-board class="dv-scr-board" :config="config" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      config: {
        header: ['当月排名','名称', '得分'],
        data: [
          ['1','新余市金车精测电子科技有限公司', 13],
          ['2','江西中邦电子科技有限公司', 15],
          ['3','江西盛泰精密光学有限公司', 10],
          ['4','中联神农高科技有限公司', 5],
          ['4','中联神农高科技有限公司',12],
          ['5','逊强贸易有限公司', 11],
          ['6','新余景润服饰有限公司',8],
          ['7','分宜县龙华金属回收有限公司第二门市部', 14],
          ['8','新余市汇康食品有限公司', 6],
          ['9','云桉建筑', 4],
          ['10','江西肆海电子科技有限公司', 3]
        ],
        rowNum: 7, //表格行数
        headerHeight: 20,
        headerBGC: '#0f1325', //表头
        oddRowBGC: '#0f1325', //奇数行
        evenRowBGC: '#171c33', //偶数行
        index: false,
        columnWidth: [130, 330, 100],
        align: ['center']
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$box-height: 500px;
$box-width: 565px;
#safeRanking {
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
