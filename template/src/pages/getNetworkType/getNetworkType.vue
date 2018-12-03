<template>
    <div class="container">
        <div class="page-body">
            <div class="title">当前网络状态</div>
            <div class="page-info">\{{networkType}}</div>
            <button class="btn" @click="getNetworkType" type="primary" hover-stop-propagation="true">点击获取网络状态</button>
            <button @click="clearClick" hover-stop-propagation="true">清空</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "getNetworkType",
      data() {
        return {
            title: 'getNetworkType',
            networkType: '未获取'
        }
      },
      methods: {
          getNetworkType() {
              duv.getNetworkType({
                  success: res => {
                      this.setData({
                          'networkType': res.networkType
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '获取网络状态失败'
                      });
                  }
              });
          },

          clearClick(e) {
              this.setData({
                  'networkType': '未获取'
              });
          }
      }
  }
</script>

<style>

    .page-body {
        margin-top: 0;
    }

    .page-info {
        height: 83px;
        line-height: 83px;
        background-color: #fff;
        color: #000;
        font-size: 30px;
        text-align: center;
    }

    swan-button {
        margin-top: 15px;
    }

</style>
