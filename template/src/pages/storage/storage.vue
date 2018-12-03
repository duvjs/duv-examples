<template>
    <div class="container">
        <div class="page-body">
            <input @input="keyInput" class="input" type="text" placeholder="请输入key"/>
            <input @input="valueInput" class="input" type="text" placeholder="请输入value"/>
            <button @click="setStorage" type="primary" hover-stop-propagation="true">存储数据</button>
            <button @click="getStorage" type="primary" hover-stop-propagation="true">读取数据</button>
            <button @click="clearStorage" hover-stop-propagation="true">清理数据</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "storage",
      data() {
        return {
            title: 'get/set/clearStorage',
            key: '',
            value: '',
            keyValue: ''
        }
      },
      methods: {
          keyInput(e) {
              this.setData({
                  'key': e.detail.value
              });
          },

          valueInput(e) {
              this.setData({
                  'value': e.detail.value
              });
          },

          setStorage() {
              let key = this.hasKey();
              if (!key) {
                  return;
              }
              duv.setStorage({
                  key,
                  data: this.value,
                  success: res => {
                      duv.showToast({
                          title: '存储数据成功'
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '存储数据失败'
                      });
                  }
              });
          },

          getStorage() {
              let key = this.hasKey();
              if (!key) {
                  return;
              }
              duv.getStorage({
                  key,
                  success: res => {
                      duv.showModal({
                          title: '读取数据成功',
                          content: JSON.stringify(res),
                          showCancel: false
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '读取数据失败'
                      });
                  }
              });
          },

          clearStorage() {
              duv.clearStorageSync();
              console.log('why', this.keyValue);
              this.setData({
                  'keyValue': ''
              });
              duv.showToast({
                  title: '清除数据成功'
              });
          },

          hasKey() {
              let key = this.key;
              if (key) {
                  return key;
              }
              duv.showToast({
                  title: 'key不能为空'
              });
          }
      }
  }
</script>

<style>
    swan-button {
        margin-top: 30rpx;
    }
</style>
