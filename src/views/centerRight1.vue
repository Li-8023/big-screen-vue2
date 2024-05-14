<template>
  <div id="centerRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' style="font-size: 20px;"></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2" style="font-size: 20px;">企业得分排行榜</span>
          
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
        header: ['当月排名','名称', '得分', '评价类别'],
        rowNum: 16, //表格行数
        headerHeight: 20,
        headerBGC: '#0f1325', //表头
        oddRowBGC: '#0f1325', //奇数行
        evenRowBGC: '#171c33', //偶数行
        index: false,
        columnWidth: [100, 300, 100, 100],
        align: ['center']
      },
       originalData: [
          ['1','新余市金车精测电子科技有限公司', '106', "A"],
          ['2','江西中邦电子科技有限公司', '105', "A"],
          ['3','江西盛泰精密光学有限公司', '103', "B"],
          ['4','中联神农高科技有限公司', '102', "B"],
          ['5','逊强贸易有限公司', '101', "B"],
          ['6','新余景润服饰有限公司', '99', "B"],
          ['7','分宜县龙华金属回收有限公司第二门市部', '98', "B"],
          ['8','新余市汇康食品有限公司', '96', "C"],
          ['9','云桉建筑', '96', "C"],
          ['10','江西肆海电子科技有限公司', '93', "C"],
          ['11','新余市金车精测电子科技有限公司', '106', "C"],
          ['12','江西中邦电子科技有限公司', '105', "C"],
          ['13','江西盛泰精密光学有限公司', '103', "C"],
          ['14','中联神农高科技有限公司', '102', "A"],
          ['15','中联神农高科技有限公司', '102', "A"],
          ['16','逊强贸易有限公司', '101', "D"],
          ['17','新余景润服饰有限公司', '99', "D"],
          ['18','分宜县龙华金属回收有限公司第二门市部', '98', "D"],
          ['19','云桉建筑', '96', "D"],
          ['20','江西肆海电子科技有限公司', '93', "D"],
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
$box-height: 930px;
$box-width: 760px;
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
      height: 800px;
    }
  }
  .d-flex{
    margin-bottom: 10px;
  }
}
</style>
