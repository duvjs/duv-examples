<template>
    <div class="container">
        <div class="page-body">
            <button @click="showActionSheet" class="button" type="default" hover-stop-propagation="true">弹出action sheet</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>

</template>

<script>
  export default {
    name: "showActionSheet",
      data() {
        return {
            title: 'action-sheet'
        }
      },
      methods: {
          showActionSheet() {
              duv.showActionSheet({
                  itemList: ['选项一', '选项二', '选项三', '选项四'],
                  itemColor: '#333',
                  success: res => {
                      console.log('用户点击了第' + (res.tapIndex + 1) + '个按钮');
                  }
              });
          }
      }
  }
</script>

<style>

    .button {
        color: #333;
        font-size: 36rpx;
    }
    .button::after {
        border-color: #999;
    }
    .page-title-line {
        width: 170rpx;
    }
</style>
