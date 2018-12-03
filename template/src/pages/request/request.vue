<template>
    <div class="container">
        <div class="page-body">
            <button @click="request" type="primary" :loading="loading" hover-stop-propagation="true">点击发起请求</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
      config: {
          "navigationBarTitleText": "发起请求"
      },
    name: "request",
      data () {
          return {
              title: 'request',
              loading: false
          }
      },
      methods: {
          request() {
              this.setData({
                  'loading': true
              });
              duv.request({
                  url: 'https://sfc.baidu.com/shopping/nianhuo/bimai',
                  data: {
                      tabname: '美食酒水'
                  },
                  success: res => {
                      duv.showToast({
                          title: '请求成功',
                          icon: 'success'
                      });
                      console.log('request success', res);
                  },
                  fail: err => {
                      duv.showToast({
                          title: JSON.stringify(err)
                      });
                      console.log('request fail', err);
                  },
                  complete: () => {
                      this.setData({
                          'loading': false
                      });
                  }
              });
          }
      }
  }
</script>

<style scoped>

</style>
