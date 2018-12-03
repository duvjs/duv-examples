<template>
    <div class="container">
        <div class="page-body">
            <button @click="showModal" type="primary" hover-stop-propagation="true">有标题的modal</button>
            <button @click="showModalNotitle" type="primary" hover-stop-propagation="true">无标题的modal</button>
            <!-- <button bind:tap="showModalNotitle" type="primary" hover-stop-propagation="true">无取消按钮的弹窗</button> -->
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>

</template>

<script>
  export default {
    name: "modal",
      data() {
        return {
            title: 'modal'
        }
      },
      methods: {
          showModal() {
              duv.showModal({
                  title: '标题',
                  content: '提示内容、告知状态、信息和解决方法，描述尽量控制在两行内',
                  showCancel: false
              });
          },

          showModalNotitle() {
              duv.showModal({
                  content: '提示内容、告知状态、信息和解决方法，描述尽量控制在两行内',
                  confirmText: '确定',
                  cancelText: '取消'
              });
          }
      }
  }
</script>

<style>
    .page-body {
        margin-top: 284rpx;
    }

    swan-button {
        margin-bottom: 30rpx;
    }

</style>
