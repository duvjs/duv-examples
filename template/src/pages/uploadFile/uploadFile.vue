<template>
    <div class="container">
        <div class="page-body">
            <button @click="uploadFile" type="primary" hover-stop-propagation="true">点击选择图片并上传</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "uploadFile",
      data() {
        return {
            title: 'uploadFile'
        }
      },
      methods: {
          uploadFile() {
              duv.chooseImage({
                  count: 1,
                  sizeType: ['compressed'],
                  sourceType: ['album'],
                  success: res => {
                      duv.uploadFile({
                          url: 'https://smartapp.baidu.com/mappconsole/api/checkFile',
                          filePath: res.tempFilePaths[0],
                          name: 'myfile',
                          success: res => {
                              duv.showToast({
                                  title: '上传成功',
                                  icon: 'success'
                              });
                          },
                          fail: err => {
                              duv.showToast({
                                  title: '上传失败'
                              });
                          }
                      });
                  }
              });
          }
      }
  }
</script>

<style scoped>

</style>
