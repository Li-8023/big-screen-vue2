<template>
  <div id="index" ref="appRef">
    <div class="bg">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 class="dv-dec-10" />
          <div class="d-flex jc-center">
            <dv-decoration-8 class="dv-dec-8" :color="decorationColor" />
            <div class="title">
              <span class="title-text">新余市金车精测电子科技有限公司</span>
              <dv-decoration-6
                class="dv-dec-6"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
              />
            </div>
            <dv-decoration-8
              class="dv-dec-8"
              :reverse="true"
              :color="decorationColor"
            />
          </div>
          <dv-decoration-10 class="dv-dec-10-s" />
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex aside-width">
            <div class="react-left ml-4 react-l-s">
              <span class="react-left"></span>
              <span class="text"></span>
            </div>
            <div class="react-left ml-3">
              <dv-decoration-4
                :reverse="true"
                style="width: 250px; height: 5px"
              />
              <span
                v-if="!editMode"
                class="text sub-title"
                @click="toggleEditMode"
              >
                企业数据展示
              </span>
              <input
                v-else
                type="text"
                v-model="companyName"
                @blur="toggleEditMode"
                @keyup.enter="handleEnter"
                class="input-field text"
                placeholder="请输入公司名称"
              />
            </div>
          </div>
          <div class="d-flex aside-width">
            <div class="react-right bg-color-blue mr-3">
              <span class="text fw-b"></span>
            </div>
            <div class="react-right mr-4 react-l-s">
              <span class="react-after"></span>
              <span class="text"
                >{{ dateYear }} {{ dateWeek }} {{ dateDay }}
                <span class="icon" @click="gotoMain">
                  <i class="bx bx-power-off"></i>
                </span>
              </span>
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-6>
                <centerLeft1 />
              </dv-border-box-6>
            </div>
            <div>
              <dv-border-box-8>
                <center />
              </dv-border-box-8>
            </div>
            <div>
              <dv-border-box-8>
                <center2 />
              </dv-border-box-8>
            </div>
            <div>
              <dv-border-box-6>
                <mapView />
              </dv-border-box-6>
            </div>
          </div>

          <!-- 第四行数据 -->
          <div class="company-bottom-box">
            <dv-border-box-8>
              <bottomLeft />
            </dv-border-box-8>
            <dv-border-box-8>
              <bottomRight />
            </dv-border-box-8>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import drawMixin from "../../utils/drawMixin";
import { formatTime } from "../../utils/index.js";
import centerLeft1 from "./centerLeft1";
import bottomRight from "./bottomRight";
import center2 from "./center2";
import center from "./center";
import bottomLeft from "./bottomLeft";
import mapView from "./map.vue";

export default {
  mixins: [drawMixin],
  data() {
    return {
      timing: null,
      loading: true,
      dateDay: null,
      dateYear: null,
      dateWeek: null,
      weekday: ["周日", "周一", "周二", "周三", "周四", "周五", "周六"],
      decorationColor: ["#568aea", "#000000"],
      companyName: "",
      editMode: false,
    };
  },
  components: {
    centerLeft1,
    bottomRight,
    center,
    center2,
    bottomLeft,
    mapView,
  },
  mounted() {
    this.timeFn();
    this.cancelLoading();
  },
  beforeDestroy() {
    clearInterval(this.timing);
  },
  methods: {
    toggleEditMode() {
      this.editMode = !this.editMode;
    },
    handleEnter(event) {
      if (event.key === "Enter") {
        this.toggleEditMode();
        this.$router.push("/");
      }
    },
    gotoMain() {
      this.$router.push("/");
    },
    timeFn() {
      this.timing = setInterval(() => {
        this.dateDay = formatTime(new Date(), "HH: mm: ss");
        this.dateYear = formatTime(new Date(), "yyyy-MM-dd");
        this.dateWeek = this.weekday[new Date().getDay()];
      }, 1000);
    },
    cancelLoading() {
      setTimeout(() => {
        this.loading = false;
      }, 500);
    },
  },
};
</script>

<style lang="scss" scoped>
.bx-power-off {
  padding: 10px;
}

@import "../../assets/scss/index.scss";

.input-field {
  background-color: #0f1325;
  color: white;
  cursor: pointer;
  font-size: 18px;
  border: 1px solid #0f1325;
  box-shadow: none;
  /* Default no shadow */
}
</style>
