<template>
    <video id="myVideo" src="http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400" :controls="false" event-model="bubble">
        <cover-view class="controls">
            <cover-view class="play" @click="play">
                <cover-image class="img" src="../../images/pausing.png" />
            </cover-view>
            <cover-view class="pause" @click="pause">
                <cover-image class="img" src="../../images/playing.png" />
            </cover-view>
            <cover-view class="time">00:00</cover-view>
        </cover-view>
    </video>
</template>

<script>
  export default {
    name: "cover-view",
      data() {
        return {
            videoCtx: null
        }
      },
      mounted() {
          this.videoCtx = duv.createVideoContext('myVideo')
      },
      methods: {
          play() {
              this.videoCtx.play()
          },
          pause() {
              this.videoCtx.pause()
          }
      }
  }
</script>

<style>
    .controls {
        position: relative;
        top: 50%;
        height: 50px;
        margin-top: -25px;
        display: flex;
    }
    .play,.pause,.time {
        flex: 1;
        height: 100%;
    }
    .time {
        text-align: center;
        background-color: rgba(0, 0, 0, .5);
        color: white;
        line-height: 50px;
    }
    .img {
        width: 40px;
        height: 40px;
        margin: 5px auto;
    }
</style>
