<template>
    <div class="wrap">
        <div class="page-top">
            <div class="page-top-text">{{title}}</div>
            <div class="page-top-line"></div>
        </div>
        <div class="page-body-canvas">
            <img src="../../images/gravity.png" class="page-body-ball" />
            <canvas class="page-body-ball" :show="true" canvas-id="small-ball"></canvas>
        </div>
        <div class="page-body-xyz">
            <text class="page-body-title">X: {{x}}</text>
            <text class="page-body-title">Y: {{y}}</text>
            <text class="page-body-title">Z: {{z}}</text>
        </div>
        <div class="page-body-btn">
            <div :class="!iswatch ? 'middle-btn' : 'middle-btn disabled'" @click="startWatch">开始监听</div>
            <div :class="!iswatch ? 'middle-btn disabled' : 'middle-btn'" @click="stopWatch">停止监听</div >
        </div>
    </div>
</template>

<script>
  export default {
    name: "getGravity",
      data() {
        return {
            title: '倾斜手机即可移动下方小球',
            iswatch: true,
            x: 0,
            y: 0,
            z: 0,
            interval: null
        }
      },
      onShow() {
          let watch = this.iswatch;
          if (watch) {
              duv.startAccelerometer();
          } else {
              duv.stopAccelerometer();
          }
      },
      methods: {
          drawSmallBall() {
              let p = this.position;
              p.x = p.x + p.vx;
              p.y = p.y + p.vy;
              p.vx = p.vx + p.ax;
              p.vy = p.vy + p.ay;

              if (Math.sqrt(Math.pow(Math.abs(p.x) - 151, 2) + Math.pow(Math.abs(p.y) - 151, 2)) >= 115) {
                  if (p.x > 151 && p.vx > 0) {
                      p.vx = 0;
                  }
                  if (p.x < 151 && p.vx < 0) {
                      p.vx = 0;
                  }
                  if (p.y > 151 && p.vy > 0) {
                      p.vy = 0;
                  }
                  if (p.y < 151 && p.vy < 0) {
                      p.vy = 0;
                  }
              }
              let stx = duv.createCanvasContext('small-ball');
              stx.beginPath(0);
              stx.arc(p.x, p.y, 15, 0, Math.PI * 2);
              stx.setFillStyle('#3388FF');
              stx.fill();
              stx.draw();
          },
          startWatch() {
              let self = this;
              self.setData({
                  'iswatch': true
              });
              duv.startAccelerometer();
          },
          stopWatch() {
              this.setData({
                  'iswatch': false
              });
              duv.stopAccelerometer();

          }
      },
      mounted() {
          this.position = {
              x: 151,
              y: 151,
              vx: 0,
              vy: 0,
              ax: 0,
              ay: 0
          };
          let self = this;
          duv.onAccelerometerChange(function (res) {
              self.setData({
                  x: res.x.toFixed(2),
                  y: res.y.toFixed(2),
                  z: res.z.toFixed(2)
              });
              self.position.ax = Math.sin(res.x * Math.PI / 2);
              self.position.ay = -Math.sin(res.y * Math.PI / 2);

          });
          this.interval = setInterval(function () {
              self.drawSmallBall();
          }, 20);
      },
      beforeDestory() {
          this.interval && clearInterval(this.interval);
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
    .page-body-xyz {
        display: flex;
        justify-content: space-between;
        width: 600rpx;
        text-align: center;
        padding-top: 112rpx;
        color: #333;
    }
    .page-body-btn {
        display: flex;
        justify-content: space-around;
        width: 480rpx;
        text-align: center;
        padding-top: 102rpx;
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
        border-radius: .1rem;
    }
    .disabled {
        opacity: .3 !important;
    }
    /*canvas 端上支持渲染为px*/
    .page-body-canvas {
        margin-top: 118rpx;
        width: 302px;
        height: 302px;
        position: relative;

    }
    .page-body-ball {
        position: absolute;
        top: 0;
        left: 0;
        width: 302px;
        height: 302px;
    }
</style>
