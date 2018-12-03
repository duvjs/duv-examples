<template>
    <div class="container">
        <div class="page-body">
            <button @click="login" type="primary" hover-stop-propagation="true">登录</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "login",
      data() {
        return {
            title: 'login',
            hasLogin: false
        }
      },
      methods: {
          login(e) {
              duv.checkSession({
                  success: res => {
                      duv.showToast({
                          title: '您已登录'
                      });
                  },
                  fail: err => {
                      duv.login({
                          success: res => {
                              duv.showToast({
                                  title: '登录成功'
                              });
                          },
                          fail: err => {
                              duv.showToast({
                                  title: '登录失败'
                              });
                          }
                      });
                  }
              });
          }
      }
  }
</script>

<style>
    .page-body-info {
        text-align: center;
        font-size: 120rpx;
    }

</style>
