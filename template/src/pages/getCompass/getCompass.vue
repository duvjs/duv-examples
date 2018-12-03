<template>
    <view class="wrap">
        <view class="page-top">
            <view class="page-top-text">{{title}}</view>
            <view class="page-top-line"></view>
        </view>

        <view class="direction">
            <view class="bg-compass-line"></view>
            <view class="bg-compass" :style="'transform: rotate(-' + direction + 'deg)'">
                <view class="num num0" :style="'transform: rotate(' + direction + 'deg)'">0</view>
                <view class="num num90" :style="'transform: rotate(' + direction + 'deg)'">90</view>
                <view class="num num180" :style="'transform: rotate(' + direction + 'deg)'">180</view>
                <view class="num num270" :style="'transform: rotate(' + direction + 'deg)'">270</view>
            </view>
            <div class="cg-wrap">
                <div class="circle-left-wrap"><div class="circle-left" :style="'transform:rotate(' + leftdeg + 'deg);transform-origin:50% 50%'"></div></div>
                <div class="circle-right-wrap"><div class="circle-right" :style="'transform:rotate(' + rightdeg + 'deg);transform-origin:50% 50%'"></div></div>
                <div class="mask">
                    <view class="direction-num">
                        <text>{{direction}}</text>
                        <text class="direction-degree"></text>
                    </view>
                </div>
            </div>
        </view>
        <view class="page-body-btn">
            <view :class="!iswatch ? 'middle-btn' : 'middle-btn disabled'" @click="startWatch">开始监听</view>
            <view :class="!iswatch ? 'middle-btn disabled' : 'middle-btn'" @click="stopWatch">停止监听</view >
        </view>
        <view>{{res}}</view>
    </view>
</template>

<script>
  export default {
    name: "getCompass",
      data() {
        return {
            title: '旋转手机即可以获取方位信息',
            direction: 0,
            iswatch: true,
            leftdeg: 0,
            rightdeg: 0
        }
      },
      created() {
          let that = this;
          duv.onCompassChange(function (res) {
              that.setData({
                  direction: parseInt(res.direction, 10)
              });
              that.updateProgress(res.direction);
          });
      },
      onShow() {
          let watch = this.iswatch;
          if (watch) {
              duv.startCompass();
          } else {
              duv.stopCompass();
          }
      },
      methods: {
          startWatch() {
              this.setData({
                  'iswatch': true
              });
              duv.startCompass();
          },
          stopWatch() {
              this.setData({
                  'iswatch': false
              });
              duv.stopCompass();
          },
          updateProgress(direction) {
              let leftdeg;
              let rightdeg;
              let deg = +direction;
              if (deg > 180) {
                  leftdeg = 180;
                  rightdeg = 180 - deg;
              } else {
                  leftdeg = -deg;
                  rightdeg = 0;
              }
              this.setData({
                  leftdeg: leftdeg,
                  rightdeg: rightdeg
              });
          }
      }
  }
</script>

<style>
    .wrap {
        background-color: #fff;
        font-size: 30rpx;
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .direction {
        position: relative;
        margin-top: 120rpx;
        width: 630rpx;
        height: 630rpx;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .num {
        position: absolute;
        color: #999;
        font-size: 26rpx;
    }
    .num0 {
        top: -30rpx;
        left: 49%;
    }
    .num90 {
        top: 46.5%;
        right: -40rpx;
    }
    .num180 {
        bottom: -40rpx;
        left: 46.5%;
    }
    .num270 {
        left: -40rpx;
        top: 46.5%;
    }
    .bg-compass {
        position: relative;
        width: 630rpx;
        height: 630rpx;
        background: url(../../images/compass.png) no-repeat center;
        background-size: contain;
    }
    .bg-compass-line {
        position: absolute;
        left: 312rpx;
        top: -10rpx;
        width: 6rpx;
        height: 80rpx;
        /*background: url(../../images/blue-bar.png) no-repeat center;*/
        background-size: contain;
        z-index: 1;
    }
    .direction-value {
        position: absolute;
    }
    .direction-num {
        position: relative;
        color: #333;
        line-height: 1;
        font-size: 186rpx;
        z-index: 2;
    }
    .direction-degree {
        position: absolute;
        top: 0;
        right: -20rpx;
        width: 30rpx;
        height: 30rpx;
        border: 8rpx solid #333;
        border-radius: 50% 50%;
    }
    .page-body-xyz {
        display: flex;
        justify-content: space-between;
        width: 600rpx;
        text-align: center;
        padding-top: 82rpx;
        color: #333;
    }
    .page-body-btn {
        display: flex;
        justify-content: space-around;
        width: 480rpx;
        text-align: center;
        padding-top: 170rpx;
    }
    .middle-btn {
        margin: 0 auto 30rpx;
        width: 214rpx;
        height: 88rpx;
        line-height: 88rpx;
        font-size: 30rpx;
        color: #333;
        position: relative;
        border-radius: 20rpx;
    }
    .middle-btn:before {
        content: "";
        pointer-events: none;
        box-sizing: border-box;
        position: absolute;
        width: 200%;
        height: 200%;
        left: 0;
        top: 0;
        border: 1px solid #333;
        transform: scale(0.5);
        transform-origin: 0 0;
        border-radius: 20rpx;
    }
    .disabled {
        opacity: .3 !important;
    }
    .cg-wrap {
        position: absolute;
        top: 30rpx;
        left: 30rpx;
        width: 572rpx;
        height: 572rpx;
        border-radius: 50%;
        background: #38f;
    }

    .circle-left-wrap {
        position: absolute;
        top: 0;
        left: 0;
        width: 286rpx;
        height: 572rpx;
        overflow: hidden;
    }
    .circle-right-wrap {
        position: absolute;
        top: 0;
        left: 0;
        width: 286rpx;
        height: 572rpx;
        overflow: hidden;
    }
    .circle-right-wrap {
        left: 286rpx;
    }

    .circle-left {
        position: absolute;
        top: 0;
        left: 0;
        width: 572rpx;
        height: 572rpx;
        border-radius: 50%;
        box-shadow: 0 0 2rpx 2rpx #efefef inset;
        background: #f8f8f8;
    }
    .circle-right {
        position: absolute;
        top: 0;
        left: 0;
        width: 572rpx;
        height: 572rpx;
        border-radius: 50%;
        box-shadow: 0 0 2rpx 2rpx #efefef inset;
        background: #f8f8f8;
    }
    .circle-right {
        left: -286rpx;
    }

    .circle-left {
        clip: rect(0, 286rpx, auto, 0);
    }
    .circle-right {
        clip: rect(0, auto, auto, 286rpx);
    }
    .mask {
        position: absolute;
        top: 34rpx;
        left: 34rpx;
        width: 500rpx;
        height: 500rpx;
        border-radius: 50%;
        background: #f8f8f8;
        color: #59d;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
