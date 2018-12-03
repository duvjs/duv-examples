<template>
    <div class="wrap">
        {{a}}
        <div class="chooseBox">
            <div class="chooseBtn" @click="chooseVideo" v-if="!showVideo">
                <img :src="icon" class="chooseIcon" />
                <view class="chooseText">请选择视频</view>
            </div>
            <div id="myVideo" controls :src="src" @play="playVideo" v-else></div>
        </div>
        <div class="section">
            <div class="source border-bottom border-top">
                <text>视频来源</text>
                <text>拍摄或相册</text>
            </div>
            <div class="device border-bottom">
                <text>摄像头</text>
                <text>前置或后置</text>
            </div>
            <div class="duration border-bottom">
                <text>拍摄长度</text>
                <text>{{maxDuration}}秒</text>
            </div>
        </div>
    </div>

</template>

<script>
  export default {
    name: "chooseVideo",
      data() {
        return {
            a: '1',
            sourceType: ['album', 'camera'],
            compressed: false,
            maxDuration: 60,
            src: '',
            info: '',
            icon: '../../images/cross.png',
            showVideo: false
        }
      },
      methods: {
          playVideo() {
              // swan.showToast({
              //     title: '触发bindplay'
              // });
              console.log('触发bindplay');
          },
          chooseVideo() {
              let self = this;
              duv.chooseVideo({
                  sourceType: this.sourceType,
                  compressed: this.compressed,
                  maxDuration: this.maxDuration,
                  success(res) {
                      // 成功返回选定视频的临时文件路径
                      let duration = +res.duration;
                      self.setData({
                          'src': res.tempFilePath,
                          'showVideo': true,
                          'maxDuration': duration.toFixed(1)
                      });
                  },
                  fail(err) {
                      console.log('错误码：' + err.errCode);
                      console.log('错误信息：' + err.errMsg);
                  }
              });
          }
      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
        height: 100%;
    }
    .chooseBox {
        width: 100%;
        height: 448rpx;
        background: #fafafa;
        text-align: center;
        margin: 160rpx 0 40rpx;
    }
    .chooseBtn {
        padding-top: 160rpx;
        color: #666;
        font-size: 30rpx;
    }
    .chooseIcon {
        width: 86rpx;
        height: 86rpx;
        color: #999;
        margin-bottom: 42rpx;
    }
    #myVideo {
        width: 76rpx;
    }
    .source {
        text-align: left;
        font-size: 36rpx;
        display: flex;
        justify-contnet: center;
        align-items: center;
        height: 96rpx;
        padding-left: 34rpx;
    }
    .device {
        text-align: left;
        font-size: 36rpx;
        display: flex;
        justify-contnet: center;
        align-items: center;
        height: 96rpx;
        padding-left: 34rpx;
    }
    .duration {
        text-align: left;
        font-size: 36rpx;
        display: flex;
        justify-contnet: center;
        align-items: center;
        height: 96rpx;
        padding-left: 34rpx;
    }
    .source text {
        display: inline-block;
        padding-right: 70rpx;
    }
    .duration text {
        display: inline-block;
        padding-right: 70rpx;
    }
    .device text {
        display: inline-block;
        padding-right: 106rpx;
    }
</style>
