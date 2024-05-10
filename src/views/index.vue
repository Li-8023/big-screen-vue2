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
                <select v-model="searchQuery" class="custom-select" style="width:400px; height: 20px;">
                  <option value="">请选择公司名称</option>
                  <option value="江西盛泰精密光学有限公司">江西盛泰精密光学有限公司</option>
                  <option value="新余市汇康食品有限公司">新余市汇康食品有限公司</option>
                  <option value="中联神农高科技有限公司">中联神农高科技有限公司</option>
                  <option value="新余景润服饰有限公司">新余景润服饰有限公司</option>
                  <!-- <option v-for="item in companyOptions" :key="item.id" :value="item.name">{{ item.name }}</option> -->
                </select>
                </dv-border-box-8>
              </span>
              
            </div>
            <div class="react-left ml-3">
              <span class="text sub-title" @click="gotoDetail">企业数据展示</span>
            </div>
          </div>
          <div class="d-flex aside-width">
            <div class="react-right bg-color-blue mr-3">
              <span class="text fw-b">标题3</span>
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
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-10>
                <centerLeft1 />
              </dv-border-box-10>
            </div>
            <div>
              <dv-border-box-8>
                <centerLeft2 />
              </dv-border-box-8>
            </div>
            <!-- 中间 -->
            <div>
              <center />
            </div>
            <!-- 中间 -->
            <div>
              <centerRight2 />
            </div>
            <div>
              <dv-border-box-8>
                <centerRight1 :search-query="searchQuery"/>
              </dv-border-box-8>
            </div>
          </div>

          <!-- 第四行数据 -->
          <div class="bottom-box">
            <dv-border-box-13>
              <bottomLeft />
            </dv-border-box-13>
            <dv-border-box-8>
              <envRanking :search-query="searchQuery"/>
            </dv-border-box-8>
            <dv-border-box-8>
              <safeRanking :search-query="searchQuery"/>
            </dv-border-box-8>
          
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import drawMixin from "../utils/drawMixin";
import { formatTime } from '../utils/index.js'
import centerLeft1 from './centerLeft1'
import centerRight1 from './centerRight1'
import center from './center'
import bottomLeft from './bottomLeft'
import envRanking from './envRanking'
import safeRanking from './safeRanking'



export default {
  mixins: [ drawMixin ],
  data() {
    return {
      timing: null,
      loading: true,
      dateDay: null,
      dateYear: null,
      dateWeek: null,
      weekday: ['周日', '周一', '周二', '周三', '周四', '周五', '周六'],
      decorationColor: ['#568aea', '#000000'],
      searchQuery:''
    }
  },
  components: {
    centerLeft1,
    // centerLeft2,
    centerRight1,
    // centerRight2,
    center,
    bottomLeft,
    envRanking,
    safeRanking
    // bottomRight,
  },
  mounted() {
    this.timeFn()
    this.cancelLoading()
  },
  beforeDestroy () {
    clearInterval(this.timing)
  },
  methods: {
    gotoDetail(){
       this.$router.push('/detail');
    },
    timeFn() {
      this.timing = setInterval(() => {
        this.dateDay = formatTime(new Date(), 'HH: mm: ss')
        this.dateYear = formatTime(new Date(), 'yyyy-MM-dd')
        this.dateWeek = this.weekday[new Date().getDay()]
      }, 1000)
    },
    cancelLoading() {
      setTimeout(() => {
        this.loading = false
      }, 500)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/index.scss';

.sub-title{
  cursor: pointer;
}

.custom-select:focus{
  outline: none;
}
.custom-select {
  position: relative;
  font-family: Arial;
}

.custom-select{
  background-color: #0f1325;
  color: white;
  cursor: pointer;
  font-size: 13px;
  border: 1px solid #0f1325;
  box-shadow: none; /* Default no shadow */
  
}
// .custom-select:focus {
//   outline: none;
//   box-shadow: 0 0 5px rgba(0, 123, 255, 0.5); /* Blue glow effect */
// }



.select-selected {
  background-color: DodgerBlue;
}

</style>
