<template>
    <div class="container">
        <div class="page-body">
            <div class="phone-call-container">
                <text>请在下方输入电话号码</text>
                <input @input="phoneNumberInput" class="input" type="number" placeholder="请输入电话号码"/>
                <button @click="makePhoneCall" type="primary" hover-stop-propagation="true">拨打</button>
            </div>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "makePhoneCall",
      data() {
        return {
            title: 'makePhoneCall',
            phoneNumber: ''
        }
      },
      config: {
          navigationBarTitleText: '拨打电话'
      },
      methods: {
          phoneNumberInput(e) {
              this.setData({
                  'phoneNumber': e.detail.value
              });
          },

          makePhoneCall(e) {
              let phoneNumber = this.phoneNumber;
              if (!phoneNumber) {
                  duv.showToast({
                      title: '请输入电话号码'
                  });
                  return;
              }
              duv.makePhoneCall({
                  phoneNumber,
                  fail: err => {
                      duv.showModal({
                          title: '拨打失败',
                          content: '请检查是否输入了正确的电话号码',
                          showCancel: false
                      });
                  }
              });
          }
      }
  }
</script>

<style>
    swan-button {
        margin-top: 30rpx;
    }
    .phone-call-container {
        margin: 0 30rpx;
        padding: 60rpx 0;
        background-color: #fff;
    }
    .phone-call-container swan-text{
        margin: 20rpx 46rpx 60rpx;
        color: #666;
    }
    .phone-call-container swan-input{
        padding-left: 0;
        border-bottom: 1px solid #eee;
        box-sizing: content-box;
    }

</style>
