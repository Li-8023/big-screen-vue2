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
              <span class="title-text">分宜工业园智慧大屏</span>
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
              <span class="text">
                <dv-border-box-8>
                  <!-- <input type="text" v-model="searchQuery" placeholder="请输入公司名称"> -->
                  <select
                    v-model="searchQuery"
                    class="custom-select"
                    style="width: 400px; height: 20px"
                  >
                    <option value="">请选择企业类型</option>
                    <option value="锂电新能源">锂电新能源</option>
                    <option value="光电信息">光电信息</option>
                    <option value="装备制造">装备制造</option>
                    <option value="麻纺">麻纺</option>
                    <option value="其他">其他</option>
                    <!-- <option v-for="item in companyOptions" :key="item.id" :value="item.name">{{ item.name }}</option> -->
                  </select>
                </dv-border-box-8>
              </span>
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
                >{{ dateYear }} {{ dateWeek }} {{ dateDay }}</span
              >
            </div>
          </div>
        </div>

        <div class="body-box">
          <div class="left-part">
            <!-- Map view -->
            <div class="left">
              <!-- <mapView /> -->
              <img
                src="../assets/map.png"
                style="width: 550px; height: 430px"
              />
            </div>

            <div class="right">
              <center />
            </div>
            <div class="bottom">
              <dv-border-box-13>
                <bottomLeft :modal-active="modalActive" />
              </dv-border-box-13>
            </div>
          </div>

          <div class="right-part">
            <dv-border-box-8>
              <centerRight1
                :search-query="searchQuery"
                @modal-status-changed="handleModalStatus"
              />
            </dv-border-box-8>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import drawMixin from "../utils/drawMixin";
import { formatTime } from "../utils/index.js";
// import centerLeft1 from './centerLeft1'
// import mapView from './map.vue'
import centerRight1 from "./centerRight1";
import center from "./center";
import bottomLeft from "./bottomLeft";

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
      searchQuery: "",
      editMode: false,
      companyName: "",
      modalActive: false,
    };
  },
  components: {
    // centerLeft1,
    // mapView,
    centerRight1,
    center,
    bottomLeft,
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
        this.$router.push("/detail");
      }
    },
    handleModalStatus(status){
      this.modalActive = status;
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
@import "../assets/scss/page1.scss";

.sub-title {
  cursor: pointer;
}

.custom-select:focus {
  outline: none;
}
.custom-select {
  position: relative;
  font-family: Arial;
}

.custom-select {
  background-color: #0f1325;
  color: white;
  cursor: pointer;
  font-size: 13px;
  border: 1px solid #0f1325;
  box-shadow: none; /* Default no shadow */
}

.select-selected {
  background-color: DodgerBlue;
}

.input-field {
  background-color: #0f1325;
  color: white;
  cursor: pointer;
  font-size: 18px;
  border: 1px solid #0f1325;
  box-shadow: none; /* Default no shadow */
}
</style>
