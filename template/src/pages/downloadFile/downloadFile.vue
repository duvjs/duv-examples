<template>
    <div class="container">
        <div class="page-body">
            <button @click="downloadFile" type="primary" :loading="loading" hover-stop-propagation="true">点击下载</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "downloadFile",
      data() {
        return {
            title: 'downloadFile',
            loading: false
        }
      },
      methods: {
          downloadFile() {
              this.setData({
                  'loading': true
              });
              duv.downloadFile({
                  url: 'https://www.adobe.com/content/dam/acom/en/devnet/acrobat/pdfs/pdf_open_parameters.pdf',
                  success: res => {
                      let filePath = res.tempFilePath;
                      duv.showModal({
                          title: 'PDF文件下载完成',
                          content: '是否需要打开？',
                          success: res => {
                              if (res.confirm) {
                                  duv.openDocument({
                                      filePath,
                                      fileType: 'pdf',
                                      fail: err => {
                                          duv.showToast({
                                              title: '打开失败'
                                          });
                                      }
                                  });
                              }
                          }
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '下载失败'
                      });
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
