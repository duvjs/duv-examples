<template>
    <div class="container">
        <div class="page-body">
            <button @click="chooseImage" type="primary" hover-stop-propagation="true">点击选择图片</button>
            <button @click="previewImage" type="primary" hover-stop-propagation="true">点击预览图片</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "api-image",
      config: {
          "navigationBarTitleText": "图片"
      },
      data() {
        return {
            title: 'choose/previewImage'
        }
      },
      methods: {
          chooseImage() {
              duv.chooseImage({
                  count: 1,
                  sizeType: ['compressed'],
                  success: res => {
                      duv.showModal({
                          title: '图片选择成功',
                          content: res.tempFilePaths[0],
                          showCancel: false
                      });
                  }
              });
          },

          previewImage() {
              duv.previewImage({
                  urls: [
                      'https://b.bdstatic.com/searchbox/icms/searchbox/img/swan-preview-image.jpg',
                      'https://b.bdstatic.com/searchbox/icms/searchbox/img/swan-preview-image-2.png'
                  ]
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
