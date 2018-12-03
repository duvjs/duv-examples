<template>
    <div class="wrap">
        <!-- canvas.wxml -->
        <canvas style="width: 300px; height: 200px;" canvas-id="firstCanvas"></canvas>
        <!-- 因为 canvas-id 与前一个 canvas 重复，该 canvas 不会显示，并会发送一个错误事件到 AppService -->
        <canvas style="width: 400px; height: 500px;" canvas-id="secondCanvas" @error="canvasIdErrorCallback"></canvas>

        <canvas canvas-id="canvas" class="canvas"></canvas>

    </div>

</template>

<script>
  export default {
    name: "canvas",
      data() {
        return {
            canvasShow: false,
            canvasOff: '',
            cur: 0,
            position: [
            ],
            interval: null
        }
      },
      mounted() {
          // 使用 wx.createContext 获取绘图上下文 context
          var context = duv.createCanvasContext('firstCanvas')

          context.setStrokeStyle("#00ff00")
          context.setLineWidth(5)
          context.rect(0, 0, 200, 200)
          context.stroke()
          context.setStrokeStyle("#ff0000")
          context.setLineWidth(2)
          context.moveTo(160, 100)
          context.arc(100, 100, 60, 0, 2 * Math.PI, true)
          context.moveTo(140, 100)
          context.arc(100, 100, 40, 0, Math.PI, false)
          context.moveTo(85, 80)
          context.arc(80, 80, 5, 0, 2 * Math.PI, true)
          context.moveTo(125, 80)
          context.arc(120, 80, 5, 0, 2 * Math.PI, true)
          context.stroke()
          context.draw()


          this.position = {
              x: 150,
              y: 150,
              vx: 2,
              vy: 2
          }

          this.drawBall()
          this.interval = setInterval(this.drawBall, 17)
      },
      beforeDestory() {
          this.interval && clearInterval(this.interval)
      },
      methods: {
          canvasIdErrorCallback: function (e) {
              console.error(e.detail.errMsg)
          },
          drawBall: function () {
              var p = this.position
              p.x += p.vx
              p.y += p.vy
              if (p.x >= 300) {
                  p.vx = -2
              }
              if (p.x <= 7) {
                  p.vx = 2
              }
              if (p.y >= 300) {
                  p.vy = -2
              }
              if (p.y <= 7) {
                  p.vy = 2
              }

              var context = duv.createContext()

              function ball(x, y) {
                  context.beginPath(0)
                  context.arc(x, y, 5, 0, Math.PI * 2)
                  context.setFillStyle('#1aad19')
                  context.setStrokeStyle('rgba(1,1,1,0)')
                  context.fill()
                  context.stroke()
              }

              ball(p.x, 150)
              ball(150, p.y)
              ball(300 - p.x, 150)
              ball(150, 300 - p.y)
              ball(p.x, p.y)
              ball(300 - p.x, 300 - p.y)
              ball(p.x, 300 - p.y)
              ball(300 - p.x, p.y)

              duv.drawCanvas({
                  canvasId: 'canvas',
                  actions: context.getActions()
              })
          },
      }
  }
</script>

<style>
    .wrap {
        padding-top: 60rpx;
    }
    .canvas-wrap {
        margin: 0 46rpx;
    }
    .btn {
        margin: 30rpx 46rpx 0;
    }
    .canvas-off {
        margin-top: 200rpx;
    }
    .canvas {
        width: 305px;
        height: 305px;
        background-color: #fff;
    }

</style>
