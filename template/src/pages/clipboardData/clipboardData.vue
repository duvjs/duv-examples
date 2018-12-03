<template>
    <div class="container">
        <div class="page-body">
            <div class="page-item">
                <div class="info">{{originData}}</div>
                <button id="setClipboardData" class="btn" @click="btnClick" type="primary" hover-stop-propagation="true">复制</button>
            </div>
            <div class="page-item">
                <div class="info">{{clipboardData}}</div>
                <button id="getClipboardData" class="btn" @click="btnClick" type="primary" hover-stop-propagation="true">粘贴</button>
            </div>
        </div>

        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "clipboardData",
      data() {
        return {
            title: 'get/setClipboardData',
            items: [{
                name: '复制',
                id: 'setClipboardData'
            }, {
                name: '粘贴',
                id: 'getClipboardData'
            }],
            originData: 'baidu',
            clipboardData: ''
        }
      },
      config: {
          "navigationBarTitleText": "剪贴板"
      },
      methods: {
          btnClick(e) {
              let id = e.currentTarget.id;
              switch (id) {
                  case 'setClipboardData':
                      duv.setClipboardData({
                          data: this.originData,
                          success: res => {
                              duv.showToast({
                                  title: '复制成功'
                              });
                          },
                          fail: err => {
                              duv.showToast({
                                  title: '复制失败'
                              });
                              console.log('setClipboardData fail', err);
                          }
                      });
                      break;
                  case 'getClipboardData':
                      duv.getClipboardData({
                          success: res => {
                              this.setData({
                                  'clipboardData': res.data
                              });
                          },
                          fail: err => {
                              console.log('getClipboardData fail', err);
                          }
                      });
                      break;
              }
          }
      }
  }
</script>

<style>

.page-body {
    margin-top: 0;
}

.page-item {
    margin-top: 60rpx;
}

.info {
    height: 44px;
    line-height: 44px;
    background-color: #fff;
    color: #000;
    font-size: 18px;
    text-align: center;
}

.btn {
    margin-top: 15px;
}

</style>
