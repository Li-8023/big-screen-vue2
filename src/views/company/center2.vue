<template>
  <div id="center">
    <div class="up">
      <div
        class="bg-color-black item"
        v-for="item in titleItem"
        :key="item.title"
      >
        <p class="ml-3 fw-b"  style="font-size: 16px; color: #459bcc;">
          {{ item.title }}
           <i class='bx bx-expand-alt bx-tada bx-rotate-90 expand-icon' style="font-size: 20px;" @click="showFormula(item)"></i>
        </p>
        <div>
          <dv-digital-flop
            class="dv-dig-flop ml-1 mt-2 pl-3"
            :config="item.number"
          />
        </div>
      </div>
    </div>
    <div class="down">
      <div class="percent">
        <div class="score">
          <span class="credit-letter">95</span>
          <div class="score-text">
           <span class="text mx-2 mb-1 pl-3">总得分</span> 
          </div>
        </div>
      </div>
      <div class="percent">
        <div class="credit">
          <span class="credit-letter">A</span>
          <div class="credit-text">
           <span class="text mx-2 mb-1 pl-3">评级类别</span> 
          </div>
        </div>
      </div>
    </div>
    <!-- pop up window-->
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="showModal = false">&times;</span>
        <p>{{  selectedFormula }}</p>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      showModal: false,
      selectedFormula: '',
      titleItem: [
        {
          title: "亩均应税收入",
          number: {
            number: [120],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
        {
          title: "亩均税收",
          number: {
            number: [80],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
        {
          title: "安全得分",
          number: {
            number: [14],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
        {
          title: "环保得分",
          number: {
            number: [15],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
        {
          title: "加分",
          number: {
            number: [10],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
        {
          title: "减分",
          number: {
            number: [18],
            toFixed: 1,
            textAlign: "left",
            content: "{nt}",
            style: {
              fontSize: 26,
            },
          },
        },
      ],
    };
  },
  methods:{
    showFormula(item){
      this.selectedFormula = `计算 ${item.title} 的公式是...`;
      this.showModal = true;
    }
  }
};
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  width: 420px;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 6px;
      padding-top: 8px;
      margin-top: 8px;
      width: 33%;
      height: 70px;
      .dv-dig-flop {
        width: 200px;
        height: 30px;
      }
    }
  }
  .down {
    padding: 6px 4px;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 255px;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 5px;
    }
    .ranking {
      padding: 10px;
      width: 59%;
      .dv-scr-rank-board {
        height: 225px;
      }
    }
    .decoration{
      margin-left: 55px;
    }
    .percent {
      width: 40%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 50%;
        height: 120px;
        span {
          margin-top: 8px;
          font-size: 14px;
          display: flex;
          justify-content: center;
        }
      }
      .credit {
        width: 100%;
        
        margin-top: 130px;
      }
      .credit-letter{
        margin-left: 50px;
        color: #ffd700; 
        font-size: 160px; 
        text-shadow: 3px 3px 5px rgba(89, 222, 59, 0.888); 
      }
      .credit-text{
        margin-left: 40px;
        margin-top: 20px;
        font-size: 20px;
      }

       .score {
        width: 100%;
        
        margin-top:130px;
      }
      .score-text{
        margin-left: 70px;
        margin-top: 20px;
        font-size: 20px;
      }
    }
  }
}

.modal {
  display: block; 
  position: fixed; 
  z-index: 1; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto; 
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.4); 
}

.modal-content {
  background-color: #0e101f;
  margin: 20% auto; 
  padding: 20px;
  border: 1px solid #0e101f;
  width: 80%; 
  font-size: 30px;  
}

.close {
  color: #aaa;
  float: right;
  font-size: 40px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: white;
  text-decoration: none;
  cursor: pointer;
}

.expand-icon:hover{
  cursor: pointer;
  color: white;
}

</style>
