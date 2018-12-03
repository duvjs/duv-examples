<template>
    <div class="container">
        <div class="page-body">
            <button @click="showNavigationBarLoading" type="primary" hover-stop-propagation="true">显示加载动画</button>
            <button @click="hideNavigationBarLoading" type="primary" hover-stop-propagation="true">隐藏加载动画</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "navigationBarLoading",
      data() {
        return {
            title: 'navigationBarLoading'
        }
      },
      methods: {
          showNavigationBarLoading(e) {
              duv.showNavigationBarLoading();
          },

          hideNavigationBarLoading(e) {
              duv.hideNavigationBarLoading();
          }
      }
  }
</script>

<style>
    swan-button {
        margin-bottom: 30rpx;
    }

</style>
