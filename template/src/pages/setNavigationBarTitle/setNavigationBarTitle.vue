<template>
    <div class="container">
        <div class="page-body">
            <input @input="titleInput" class="input" type="text" placeholder="请输入页面标题并点击设置即可"/>
            <button @click="setNavigationBarTitle" type="primary" hover-stop-propagation="true">设置</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "setNavigationBarTitle",
      data() {
        return {
            title: 'setNavigationBarTitle',
            newTitle: ''
        }
      },
      methods: {
          titleInput(e) {
              this.setData({
                  'newTitle': e.detail.value
              });
          },

          setNavigationBarTitle(e) {
              let newTitle = this.newTitle;
              if (!newTitle) {
                  duv.showToast({
                      title: '请输入标题'
                  });
                  return;
              }
              duv.setNavigationBarTitle({
                  title: this.newTitle
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
