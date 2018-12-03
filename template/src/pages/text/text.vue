<template>
    <div class="wrap">
        <span>\{{text}}</span>
        <button class="btn" type="primary" @click="add">add text</button>
        <button class="btn" type="primary" @click="remove">remove text</button>
    </div>
</template>

<script>
  export default {
    name: "text",
      data() {
         let initData = '这是一段文字.'
        return {
            initData: initData,
            text: initData,
            extraLine: []
        }
      },
      methods: {
          add(e) {
              this.extraLine.push('其他文字');
              this.setData({
                  text: this.initData + this.extraLine.join(',')
              });
          },
          remove(e) {
              if (this.extraLine.length > 0) {
                  this.extraLine.pop();
                  this.setData({
                      text: this.initData + this.extraLine.join(',')
                  });
              }
          }
      }
  }
</script>

<style>
/*@bd*/
/*@bd end*/
    .wrap {
        /*width: 320rpx;*/
        font-size: 32rpx;
        padding: 20rpx;
    }
    .group {
        margin: 60rpx 40rpx 40rpx 40rpx;
    }
    .text-box {
        display: flex;
        margin-bottom: 133rpx;
    }
    .text-px {
        flex: 0 0 160rpx;
        text-align: center;
    }
    .text-20px {
        line-height: 238rpx;
    }
    .text-17px {
        line-height: 200rpx;
    }
    .text-14px {
        line-height: 178rpx;
    }
    .text-13px {
        line-height: 136rpx;
    }
    .text-content {
        background: #fff;
        padding: 20rpx;
        flex: 1;
    }
    .btn {
        margin: 14rpx 46rpx 0;
    }
    .wrap-20px {
        font-size: 40rpx;
        height: 238rpx;
    }
    .wrap-17px {
        font-size: 34rpx;
        height: 200rpx;
    }
    .wrap-14px {
        font-size: 28rpx;
        height: 178rpx;
    }
    .wrap-13px {
        font-size: 26rpx;
        height: 136rpx;
    }
    .content {
        overflow: scroll;
    }
    .content-20px {
        height: 198rpx;
    }
    .content-17px {
        height: 160rpx;
        line-height: 1.5;
    }
    .content-14px {
        height: 138rpx;
        line-height: 1.5;
    }
    .content-13px {
        height: 76rpx;
        line-height: 1.5;
    }
</style>
