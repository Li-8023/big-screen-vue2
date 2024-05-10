<template>
  <div id="centerRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' ></i>
        </span>
        <div class="d-flex">
          <!-- <span class=" text mx-2">企业得分排行榜</span> -->
          <span class="text mx-2">企业得分排行榜</span>
          
        </div>
      </div>
      <div class="d-flex jc-center body-box">
        <dv-scroll-board class="dv-scr-board" :config="scrollConfig" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['searchQuery'],
  data() {
    return {
      config: {
        header: ['当月排名','名称', '得分', '排名变化'],
        rowNum: 7, //表格行数
        headerHeight: 20,
        headerBGC: '#0f1325', //表头
        oddRowBGC: '#0f1325', //奇数行
        evenRowBGC: '#171c33', //偶数行
        index: false,
        columnWidth: [100, 300, 100, 100],
        align: ['center']
      },
       originalData: [
          ['1','新余市金车精测电子科技有限公司', '106', "<span  class='colorRed'>↑1</span>"],
          ['2','江西中邦电子科技有限公司', '105', "<span  class='colorGrass'>↓1</span>"],
          ['3','江西盛泰精密光学有限公司', '103', "<span  class='colorRed'>↑1</span>"],
          ['4','中联神农高科技有限公司', '102', "<span  class='colorRed'>↑1</span>"],
          ['4','中联神农高科技有限公司', '102', "<span  class='colorRed'>↑1</span>"],
          ['5','逊强贸易有限公司', '101', "<span  class='colorGrass'>↓4</span>"],
          ['6','新余景润服饰有限公司', '99', "<span  class='colorRed'>↑6</span>"],
          ['7','分宜县龙华金属回收有限公司第二门市部', '98', "<span  class='colorRed'>↑1</span>"],
          ['8','新余市汇康食品有限公司', '96', "<span  class='colorGrass'>↓3</span>"],
          ['9','云桉建筑', '96', "<span  class='colorGrass'>↓2</span>"],
          ['10','江西肆海电子科技有限公司', '93', "<span  class='colorRed'>↑1</span>"]
        ],
    }
  },
   computed:{
    scrollConfig(){
      return {
        ...this.config,
        data: this.filteredData
      };
    },
     filteredData() {
      if (!this.searchQuery) {
        return this.originalData; 
      }
      return this.originalData.filter(item => 
        item[1] === this.searchQuery
      );
    },
  }
}
</script>

<style lang="scss" scoped>
$box-height: 410px;
$box-width: 800px;
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
