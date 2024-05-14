<template>
  <div id="centerLeft1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <i class='bx bx-line-chart' style="font-size: 20px;"></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2" style="font-size: 20px;">基本情况</span>
          <dv-decoration-3 class="dv-dec-3" />
        </div>
      </div>
      <div class="business-card">
       
      
            <p><span>统一社会信用代码: </span> 91361027xxxxxxxx</p>
            <p><span>企业名称: </span> 江西省xxx有限公司</p>
            <p><span>所属行业:</span> 新能源</p>
            <p><span>企业负责人: </span> 吴xx</p>
            <p><span>企业联系电话: </span> 135xxxxxxxx</p>
            <p><span>地址: </span> 江西省新余市分宜县</p>
            <p><span>是否为规上企业：</span>是</p>
            <p><span>企业简介：</span>新余市金车精测电子科技有限公司，成立于2020-04-24，位于江西省新余市，是一家以从事计算机、通信和其他电子设备制造业为主的企业。企业目前的经营状态为存续，注册资本为100万人民币，统一社会信用代码为91360521MA397CX874</p>
       
       
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrCode: require('@/assets/QR_CODE.jpg'),
    }
  },
  mounted() {
    this.changeTiming()
  },
  methods: {
    changeTiming() {
      setInterval(() => {
        this.changeNumber()
      }, 3000)
    },
    changeNumber() {
      this.numberData.forEach((item, index) => {
        item.number.number[0] += ++index
        item.number = { ...item.number }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
$box-width: 500px;
$box-height: 410px;

.text {
  font-size: 16px;
  /* Increase text size */
}

.business-card {
  align-items: left;
  margin-left: -10px;
  color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  width: 500px;
}

.content {
  display: flex;
  margin-top: 30px;
}

.business-card p {
  margin-bottom: 15px;
  color: #ffffff;
  font-size: 16px;
}


.business-card p span {
  color: #0e92b8;
  font-size: 18px;
  font-weight: 800;
}

#centerLeft1 {
  padding: 16px;
  height: $box-height;
  width: $box-width;
  border-radius: 10px;

  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
  }

  .text {
    color: #c3cbde;
  }

  .dv-dec-3 {
    position: relative;
    width: 100px;
    height: 20px;
    top: -3px;
  }

  .bottom-data {
    .item-box {
      &>div {
        padding-right: 5px;
      }

      font-size: 14px;
      float: right;
      position: relative;
      width: 50%;
      color: #d3d6dd;

      .dv-digital-flop {
        width: 120px;
        height: 30px;
      }

      // 金币
      .coin {
        position: relative;
        top: 6px;
        font-size: 20px;
        color: #ffc107;
      }

      .colorYellow {
        color: yellowgreen;
      }

      p {
        text-align: center;
      }
    }
  }
}
</style>
