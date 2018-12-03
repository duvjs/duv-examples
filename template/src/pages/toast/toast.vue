<template>
    <div class="container">
        <div class="page-body">
            <button @click="showToast" type="primary" hover-stop-propagation="true">点击弹出默认toast</button>
            <button @click="showToastIcon" type="primary" hover-stop-propagation="true">点击弹出设置icon的toast</button>
            <button @click="showToastDuration" type="primary" hover-stop-propagation="true">点击弹出设置duration的toast</button>
            <button @click="showToastLoading" type="primary" hover-stop-propagation="true">点击弹出显示loading的toast</button>
            <button @click="hideLoading" type="primary" hover-stop-propagation="true">点击隐藏loading</button>
            <button @click="hideToast" type="primary" hover-stop-propagation="true">点击隐藏toast</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "toast",
      data() {
        return {
            title: 'toast'
        }
      },
      onHide() {
          duv.hideToast();
      },
      methods: {


          showToast() {
              duv.showToast({
                  title: '默认'
              });
          },

          showToastIcon() {
              duv.showToast({
                  title: 'success',
                  icon: 'success'
              });
          },

          showToastDuration() {
              duv.showToast({
                  duration: 5000,
                  title: 'duration 5000'
              });
          },

          showToastLoading() {
              duv.showLoading({
                  title: 'loading'
              });
          },

          hideLoading() {
              duv.hideLoading();
          },

          hideToast() {
              duv.hideToast();
          }
      }
  }
</script>

<style>
    swan-button {
        margin-bottom: 30rpx;
    }

</style>
