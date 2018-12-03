<template>
    <div class="container">
        <div class="page-body">
            <div class="title">当前网络状态</div>
            <div class="page-info">\{{networkType}}</div>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "onNetworkStatusChange",
      data() {
        return {
            title: 'onNetworkStatusChange',
            networkType: '未获取'
        }
      },
      created() {
          let self = this;
          duv.getNetworkType({
              success: res => {
                  self.setData({
                      'networkType': res.networkType
                  });
              }
          });
          duv.onNetworkStatusChange(function (res) {
              self.setData({
                  'networkType': res.networkType
              });
          });
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

</style>
