<template>
    <div class="container">
        <div class="page-body">
            <button @click="requestPolymerPayment" type="primary" hover-stop-propagation="true">支付0.01元</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "payment",
      data() {
        return {
            title: 'requestPolymerPayment'
        }
      },
      methods: {
          requestPolymerPayment(e) {
              duv.showToast({
                  title: '次功能需要配合后端调试'
              });
              // duv.request({
              //     url: 'https://mbd.baidu.com/ma/nuomi/createorder',
              //     success: res => {
              //         let data = res.data;
              //         if (data.errno !== 0) {
              //             console.log('create order err', data);
              //             return;
              //         }
              //
              //         duv.requestPolymerPayment({
              //             orderInfo: data.data,
              //             bannedChannels: this.getData('bannedChannels'),
              //             success(res) {
              //                 swan.showToast({
              //                     title: '支付成功',
              //                     icon: 'success'
              //                 });
              //             },
              //             fail(err) {
              //                 swan.showToast({
              //                     title: err.errMsg
              //                 });
              //                 console.log('pay fail', err);
              //             }
              //         });
              //     },
              //     fail: err => {
              //         duv.showToast({
              //             title: '订单创建失败'
              //         });
              //         console.log('create order fail', err);
              //     }
              // });
          }
      }
  }
</script>

<style scoped>

</style>
