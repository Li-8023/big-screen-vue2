<template>
  <div id="centerLeft1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
         <span>
          <i class='bx bx-line-chart' ></i>
        </span>
        <div class="d-flex">
          <span class="text mx-2">基本情况</span>
          <dv-decoration-3 class="dv-dec-3" />
        </div>
      </div>
      <div class="business-card">
    <div class="content">
      <img :src="qrCode" alt="QR Code" class="qr-code">
      <div class="details">
        <p> <span>组织代码: </span> 91361027xxxxxxxx</p>
        <p> <span>企业名称: </span> 江西省xxx有限公司</p>
        <p><span>所属行业:</span>  新能源</p>
        <p><span>企业负责人: </span> 吴xx</p>
        <p><span>企业联系电话: </span> 135xxxxxxxx</p>
        <p><span>地址: </span> 江西省新余市分宜县</p>
      </div>
    </div>
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
  font-size: 16px; /* Increase text size */
}
.business-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: -10px;
  color: #ffffff; /* White text color as seen in the image */
  padding: 20px;
  border-radius: 8px;
  width: 500px;
}

.content {
  display: flex;
  margin-top: 45px;
}

.qr-code {
  width: 200px;
  height: 200px;
  margin-right: 20px;
}

.details {
  display: flex;
  flex-direction: column;
}

.details p {
  margin-bottom: 15px; /* Adds space between paragraphs */
  color: #ffffff; /* Ensures text is white */
  font-size: 15px; /* Adjust font size as needed */
}


.details p span {

  color: #0e92b8; /* Ensures text is white */
   font-size: 15px; 
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
      & > div {
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
