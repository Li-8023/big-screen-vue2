<template>
  <div id="center">
    <div class="up">
      <div
        class="bg-color-black item"
        v-for="item in titleItem"
        :key="item.title"
      >
        <p class="ml-3 fw-b" style="font-size: 18px; color: #459bcc;">{{ item.title }}</p>
        <div>
          <dv-digital-flop
            class="dv-dig-flop ml-1 mt-2 pl-3"
            :config="item.number"
          />
        </div>
      </div>
    </div>
    <div class="down">
      <div class="ranking bg-color-black">
        <span>
         <i class='bx bx-objects-horizontal-left' style="font-size: 20px;"></i>
        </span>
        <span class="text mx-2 mb-1 pl-3" style="font-size: 20px;">用电量</span>
        <dv-scroll-ranking-board class="dv-scr-rank-board mt-2" :config="ranking" style="width:530px"/>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      titleItem: [
        {
          title: '总企业数',
          number: {
            number: [120],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '园区平均总得分',
          number: {
            number: [80],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '总应税收入',
          number: {
            number: [14],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '总税收',
          number: {
            number: [15],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '安全平均得分',
          number: {
            number: [10],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '环保平均得分',
          number: {
            number: [18],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '总用电量',
          number: {
            number: [3000],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '规上企业数',
          number: {
            number: [54],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
        {
          title: '规下企业数',
          number: {
            number: [31],
            toFixed: 1,
            textAlign: 'left',
            content: '{nt}',
            style: {
              fontSize: 24
            }
          }
        },
      ],
      ranking: {
        rowNum: 4,
        data: [
          {
            name: '新余市金车精测电子科技有限公司',
            value: 55
          },
          {
            name: '江西中邦电子科技有限公司',
            value: 120
          },
          {
            name: '江西盛泰精密光学有限公司',
            value: 78
          },
          {
            name: '中联神农高科技有限公司',
            value: 66
          },
          {
            name: '逊强贸易有限公司',
            value: 80
          },
          {
            name: '新余景润服饰有限公司',
            value: 80
          },
          {
            name: '分宜县龙华金属回收有限公司第二门市部',
            value: 80
          },
          {
            name: '新余市汇康食品有限公司',
            value: 80
          },
          {
            name: '云桉建筑',
            value: 80
          },
          {
            name: '江西肆海电子科技有限公司',
            value: 80
          }
        ],
        carousel: 'single',
        unit: '千瓦/时'
      },
    }
  },
}
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  width: 570px;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 6px;
      padding-top: 8px;
      margin-top: 8px;
      width: 32%;
      height: 60px;
      .dv-dig-flop {
        width: 150px;
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
      width: 100%;
      .dv-scr-rank-board {
        height: 200px;
      }
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
      .water {
        width: 100%;
        .dv-wa-le-po {
          height: 120px;
        }
      }
    }
  }
}
</style>
