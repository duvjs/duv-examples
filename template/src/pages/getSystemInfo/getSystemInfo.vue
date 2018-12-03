<template>
    <div class="container">
        <div class="page-body">
            <div class="info-ctn">
                <div class="info-item" v-for="(item, key) in infoList" :key="key">
                    <text class="info-label">{{item.label}}：</text>
                    <text class="info-value">{{item.value}}</text>
                </div>
            </div>
            <div class="btn-ctn">
                <button @click="getSystemInfo" type="primary" hover-stop-propagation="true">点击获取系统信息</button>
                <button @click="clearClick" hover-stop-propagation="true">清空</button>
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
    name: "getSystemInfo",
      data() {
        return {
            title: 'getSystemInfo',
            infoList: [{
                label: '手机品牌',
                key: 'brand',
                value: ''
            }, {
                label: '手机型号',
                key: 'model',
                value: ''
            }, {
                label: '当前版本',
                key: 'version',
                value: ''
            }, {
                label: '屏幕宽度',
                key: 'screenWidth',
                value: ''
            }, {
                label: '屏幕高度',
                key: 'screenHeight',
                value: ''
            }, {
                label: 'DPI',
                key: 'pixelRatio',
                value: ''
            }, {
                label: '语言',
                key: 'language',
                value: ''
            }]
        }
      },
      methods: {
          getSystemInfo(e) {
              duv.getSystemInfo({
                  success: res => {
                      // 更新数据
                      this.updateInfoList(res);
                  },
                  fail: err => {
                      duv.showToast({
                          title: '获取失败'
                      });
                  }
              });
          },

          clearClick() {
              this.updateInfoList({});
          },

          updateInfoList(res) {
              let infoList = this.infoList;
              for (let i = 0; i < infoList.length; ++i) {
                  infoList[i].value = res[infoList[i].key];
              }
              this.setData({
                  'infoList': infoList
              });
          }
      }
  }
</script>

<style>

    .page-body {
        margin-top: 0;
    }

    .info-ctn {
        margin-top: 30px;
        font-size: 18px;
        color: #333;
        background-color: #fff;
        padding: 0 18px;
    }

    .info-item {
        padding: 12px 0;
        border-bottom: 1px solid #f5f5f5;
        display: flex;
        align-items: center;
    }

    .info-label {
        font-size: 18px;
        color: #333;
        min-width: 95px;
        flex: 1;
    }

    .info-value {
        flex: 3;
    }

    .btn-ctn {
        margin-top: 42px;
    }

    swan-button {
        margin-bottom: 15px;
    }

</style>
