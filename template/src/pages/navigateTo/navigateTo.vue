<template>
    <div class="container">
        <div class="page-body">
            <button @click="navigateTo" type="primary" hover-stop-propagation="true">跳转新页面</button>
            <button @click="navigateBack" type="primary" hover-stop-propagation="true">返回上一页</button>
            <button @click="redirectTo" type="primary" hover-stop-propagation="true">在当前页面打开</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "navigateTo",
      data() {
        return {
            title: 'navigateTo/Back,redirectTo'
        }
      },
      methods: {
          navigateTo(e) {
              duv.navigateTo({
                  url: '/pages/detail/main'
              });
          },

          navigateBack(e) {
              duv.navigateBack({
                  delta: 2
              });
          },

          redirectTo(e) {
              duv.redirectTo({
                  url: '/pages/detail/main'
              });
          }
      }
  }
</script>

<style>

    swan-button {
        margin-bottom: 30rpx;
    }

</style>
