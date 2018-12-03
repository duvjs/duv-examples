<template>
    <div class="container">
        <div class="page-body">
            <button v-for="(item, key) in items" :key="key" :id="item.id" @click="btnClick" type="primary" hover-stop-propagation="true">{{item.name}}</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "authorize",
      data() {
        return {
            title: 'authorize',
            items: [{
                name: '授权获取用户信息',
                id: 'scope.userInfo'
            }, {
                name: '授权获取位置信息',
                id: 'scope.userLocation'
            }]
        }
      },
      methods: {
          btnClick(e) {
              let scope = e.currentTarget.id;
              console.log(scope)
              duv.getSetting({
                  success(res) {
                      console.log(res)
                      if (!res.authSetting[scope]) {
                          duv.authorize({
                              scope: scope,
                              success (result) {
                                  console.log(result)
                                  // 用户已经同意小程序使用录音功能，后续调用 duv.startRecord 接口不会弹窗询问
                                  // duv.startRecord()
                              }
                          })
                      } else {
                          console.log('已经获取')
                      }
                  }
              })
          }
      }
  }
</script>

<style>
    .page-body {
        margin-top: 84rpx;
    }

    swan-button {
        margin-bottom: 30rpx;
    }
</style>
