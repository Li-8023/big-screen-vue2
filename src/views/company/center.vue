<template>
  <div id="center">
    <div class="up">
      <div
        class="bg-color-black item"
        v-for="item in titleItem"
        :key="item.title"
      >
        <p class="ml-3 colorBlue fw-b">{{ item.title }}</p>
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
          <icon name="chart-pie" class="text-icon"></icon>
        </span>
        <dv-decoration-12 style="width: 200px; height: 200px" class="decoration"/>
        <!-- <span class="text mx-2 mb-1 pl-3">年度负责人组件达标榜</span>
        <dv-scroll-ranking-board class="dv-scr-rank-board mt-1" :config="ranking" /> -->
      </div>
      <div class="percent">
        <div class="item bg-color-black">
          <span>今日任务通过率</span>
          <CenterChart
            :id="rate[0].id"
            :tips="rate[0].tips"
            :colorObj="rate[0].colorData"
          />
        </div>
        <div class="item bg-color-black">
          <span>今日任务达标率</span>
          <CenterChart
            :id="rate[1].id"
            :tips="rate[1].tips"
            :colorObj="rate[1].colorData"
          />
        </div>
        <div class="pond bg-color-black">
          <span class="text mx-2 mb-1 pl-3">企业税务信用</span>
          <dv-percent-pond
            :config="pond"
            style="width: 200px; height: 100px"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CenterChart from "@/components/echart/center/centerChartRate";

export default {
  data() {
    return {
      titleItem: [
        {
          title: "企业亩均应税收入",
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
          title: "企业总得分",
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
          title: "企业安全生产得分",
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
          title: "企业环境保护得分",
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
          title: "企业当月用电量",
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
          title: "企业当月能耗",
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
      pond: {
        value: 66,
        borderWidth: 5,
        borderRadius: 10,
        borderGap: 5,
        localGradient: true,
      },
      // 通过率和达标率的组件复用数据
      rate: [
        {
          id: "centerRate1",
          tips: 60,
          colorData: {
            textStyle: "#3fc0fb",
            series: {
              color: ["#00bcd44a", "transparent"],
              dataColor: {
                normal: "#03a9f4",
                shadowColor: "#97e2f5",
              },
            },
          },
        },
        {
          id: "centerRate2",
          tips: 40,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad",
              },
            },
          },
        },
      ],
    };
  },
  components: {
    CenterChart,
  },
};
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
      height: 70px;
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
      .pond {
        margin-left: 10px;
        width: 100%;
        .dv-wa-le-po {
          height: 120px;
        }
      }
    }
  }
}
</style>
