<template>
  <div id="centerRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
           <i class='bx bx-expand-alt bx-tada bx-rotate-90 expand-icon' style="font-size: 20px;" @click="toggleModal"></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2" style="font-size: 20px;">企业得分排行榜</span>
        </div>
       
      </div>
      <div class="d-flex jc-center body-box">
        <dv-scroll-board class="dv-scr-board" :config="scrollConfig" />
      </div>
    </div>

    <!-- Pop-up window -->
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span @click="toggleModal" class="close-button">
          <i class='bx bx-exit-fullscreen bx-tada'></i>
        </span>
        <table>
          <thead>
            <tr>
               <th v-for="header in config.header" :key="header">{{ header }}</th>
            </tr>
          </thead>
          <tbody>
             <tr v-for="(row, index) in filteredData" :key="index">
              <td v-for="(cell, cellIndex) in row" :key="cellIndex">
                <!-- <a v-if="cellIndex === 1" :href="getUrl(cell)" target="_blank">{{ cell }}</a> -->
                <a v-if="cellIndex === 1" :href="getUrl()" target="_blank">{{ cell }}</a>
                <template v-else>{{ cell }}</template>
              </td>
            </tr>
          </tbody>
        </table>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['searchQuery'],
  data() {
    return {
      showModal:false,
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
          ['21','新余市金车精测电子科技有限公司', '106', "C"],
          ['22','江西中邦电子科技有限公司', '105', "C"],
          ['23','江西盛泰精密光学有限公司', '103', "C"],
          ['24','中联神农高科技有限公司', '102', "A"],
          ['25','中联神农高科技有限公司', '102', "A"],
          ['26','逊强贸易有限公司', '101', "D"],
          ['27','新余景润服饰有限公司', '99', "D"],
          ['28','分宜县龙华金属回收有限公司第二门市部', '98', "D"],
          ['29','云桉建筑', '96', "D"],
          ['30','江西肆海电子科技有限公司', '93', "D"],
        ],
    }
  },
  methods:{
    //  getUrl(name) {
    //   return `http://example.com/profile/${name}`;
    // },
    getUrl(){
      return "http://localhost:8080/#/detail";
    },
    toggleModal(){
      this.showModal = !this.showModal;
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
  .expand-icon {
    cursor: pointer;
  }
}

.modal {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: #0e101f;
  padding: 20px;
  border-radius: 5px;
  overflow: auto; 
  max-height: 90%;
  max-width: 100%;
}

table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 50px 30px;

  th, td {
    border: 1px solid #0e101f;
    padding: 20px;
    text-align: left;
    font-size: 25px;
    background-color: #0e101f;
  }

  th {
    padding: 30px;
    font-size: 22px;
  }

  a {
    color: inherit; 
    text-decoration: underline; 
  }

  a:hover {
    color: white; 
    text-decoration: none; 
  }
}

.close-button{
  font-size: 40px;
  color:white;
  cursor:pointer;
  border-radius: 10px;
  position: fixed;
  margin-left: 1200px;
  margin-top: -10px;
}
.close-button:hover{
  color: red;
}

</style>
