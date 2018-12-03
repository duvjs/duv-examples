<template>
    <div class="wrap">
        <div class="title">横向滚动</div>
        <scroll-view
            scroll-x
            class="scroll-view"
            @scrolltoupper="toLeft"
            @scrolltolower="toRight"
            scroll-into-view="one"
            upper-threshold="1"
            lower-threshold="1"
            @scroll="myscroll"
        >
            <div id="one"   class="color-a row-view">A</div>
            <div id="two"   class="color-b row-view">B</div>
            <div id="three" class="color-c row-view">C</div>
        </scroll-view>

        <div class="title">纵向滚动</div>
        <scroll-view
            scroll-y
            class="scroll-view"
            @scrolltoupper="upper"
            @scrolltolower="lower"
            scroll-into-view="four"
            upper-threshold="10"
            lower-threshold="10"
            @scroll="myscroll"
            enable-back-to-top="true"
        >
            <div id="four" class="color-a">A</div>
            <div id="five" class="color-b">B</div>
            <div id="six"  class="color-c">C</div>
        </scroll-view>
    </div>

</template>

<script>
  export default {
    name: "scroll-view",
      data() {
        return {
            toView: 'view4',
            scrollTop: 100
        }
      },
      methods: {
          toLeft() {
              duv.showToast({
                  duration: 1000,
                  title: '到最左边了'
              });
          },
          toRight() {
              duv.showToast({
                  duration: 1000,
                  title: '到最右边了'
              });
          },
          upper() {
              duv.showToast({
                  duration: 1000,
                  title: '到顶了'
              });
          },

          lower() {
              duv.showToast({
                  duration: 1000,
                  title: '到底了'
              });
          },

          myscroll(e) {
              console.log('获取滚动事件的详细信息e.detail：' + e.detail);
              console.dir(e.detail);
          }
      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
    }
    .scroll-view {
        height: 332rpx;
        white-space: nowrap;
        padding: 0 50rpx;
        font-size: 0;
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .color-a,
    .color-b,
    .color-c {
        height: 332rpx;
        line-height: 332rpx;
        text-align: center;
        font-size: 32rpx;
        color: #fff;
    }

    .color-a {
        background-color: #6895FF;
    }
    .color-b {
        background-color: #8FB1FF;
    }
    .color-c {
        background-color: #C3D1FF;
    }

    .row-view {
        display: inline-block !important;
        width: 100%;
        height: 332rpx;
        line-height: 332rpx;
        font-size: 20px;
    }

</style>
