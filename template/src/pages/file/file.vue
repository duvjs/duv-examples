<template>
    <div class="container">
        <div class="page-body">
            <button @click="saveFile" type="primary" hover-stop-propagation="true">下载并保存文件</button>
            <button @click="openDocument" type="primary" hover-stop-propagation="true">打开文件</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "file",
      config: {
          "navigationBarTitleText": "文件"
      },
      data() {
        return {
            title: 'saveFile/openDocument',
            filePath: ''
        }
      },
      methods: {
          saveFile() {
              duv.showToast({
                  title: '开始下载'
              });
              duv.downloadFile({
                  header: {
                      'Cache-Control': 'no-cache'
                  },
                  url: 'https://www.adobe.com/content/dam/acom/en/devnet/acrobat/pdfs/pdf_open_parameters.pdf',
                  success: res => {
                      duv.saveFile({
                          tempFilePath: res.tempFilePath,
                          success: res => {
                              duv.showToast({
                                  title: '保存成功'
                              });
                              this.setData({
                                  'filePath': res.savedFilePath
                              });
                          },
                          fail: err => {
                              duv.showToast({
                                  title: '保存失败'
                              });
                          }
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '下载失败'
                      });
                  }
              });
          },

          openDocument() {
              duv.openDocument({
                  filePath: this.filePath,
                  fileType: 'pdf',
                  fail: err => {
                      if (!this.filePath) {
                          duv.showToast({
                              title: '请先点击保存文件'
                          });
                          return;
                      }
                      duv.showToast({
                          title: '打开失败'
                      });
                  }
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
