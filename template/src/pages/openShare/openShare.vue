<template>
    <div class="container">
        <div class="page-body">
            <button type="primary" open-type="share" hover-stop-propagation="true">点击打开分享</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "openShare",
      data() {
        return {
            title: 'openShare'
        }
      },
      onShareAppMessage() {
          return {
              title: '小程序标题',
              content: '世界很复杂，百度更懂你',
              imageUrl: 'http://imgsrc.baidu.com/forum/pic/item/d9f9d72a6059252daecdfc36309b033b5bb5b92e.jpg',
              path: '/pages/openShare/openShare',
              success(res) {
                  // 分享成功
              },
              fail(err) {
                  // 分享失败
              }
          };
      }
  }
</script>

<style scoped>

</style>
