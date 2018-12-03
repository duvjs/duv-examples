<template>
    <div class="wrap">
        <video id="myVideo" :src="src" @error="videoErrorCallback"
               :danmu-list="danmuList"
               :autoplay="autoplay"
               :muted="muted"
               @pause="pause"
               @ended="ended"
               enable-danmu danmu-btn controls></video>

        <div>
            <div>
                <div class="weui-cell__hd">
                    <div>弹幕内容</div>
                </div>
                <div>
                    <input @blur="bindInputBlur" type="text" placeholder="在此处输入弹幕内容" />
                </div>
            </div>
        </div>
        <div class="btn-area">
            <button @click="bindSendDanmu" class="btn" type="primary" formType="submit">发送弹幕</button>
            <button @click="bindPlay" class="btn" type="primary">播放</button>
            <button @click="bindPause" class="btn" type="primary">暂停</button>
            <button class="btn" @click="setmuted" type="primary">设置静音</button>
            <!--<button class="btn" @click="next" type="primary">切换视频地址</button>-->
        </div>
    </div>

</template>

<script>
    /**
     * https://developers.weixin.qq.com/community/develop/doc/0008a623694f78b04217a48405b400
     * 微信小程序bug: video拖动进度条开发工具报错，不影响使用
     */

    function getRandomColor () {
        const rgb = []
        for (let i = 0 ; i < 3; ++i){
            let color = Math.floor(Math.random() * 256).toString(16)
            color = color.length == 1 ? '0' + color : color
            rgb.push(color)
        }
        return '#' + rgb.join('')
    }
  export default {
    name: "video",
      data() {
        return {
            inputValue: '',
            current: 0,
            srcList: [
                'https://vd3.bdstatic.com/mda-ia8e6q3g23py8qdh/hd/mda-ia8e6q3g23py8qdh.mp4?playlist=%5B%22hd%22%5D&auth_key=1521549485-0-0-d5d042ba3555b2d23909d16a82916ebc&bcevod_channel=searchbox_feed&pd=share',
                'https://vd3.bdstatic.com/mda-ib0u8x1bvaf00qa8/mda-ib0u8x1bvaf00qa8.mp4?playlist=%5B%22hd%22%2C%22sc%22%5D'
            ],
            // src: 'https://vd3.bdstatic.com/mda-ia8e6q3g23py8qdh/hd/mda-ia8e6q3g23py8qdh.mp4?playlist=%5B%22hd%22%5D&auth_key=1521549485-0-0-d5d042ba3555b2d23909d16a82916ebc&bcevod_channel=searchbox_feed&pd=share',
            srcList: ['http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400'],
            src: 'http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400',
            danmuList:
                [{
                    text: '第 1s 出现的弹幕',
                    color: '#ff0000',
                    time: 1
                },
                    {
                        text: '第 3s 出现的弹幕',
                        color: '#ff00ff',
                        time: 3
                    }],
            videoContext:  null,
            muted: false,
            autoplay: false
        }
      },
      mounted: function (res) {
          this.videoContext = duv.createVideoContext('myVideo')
      },
      methods: {
          bindInputBlur: function(e) {
              this.inputValue = e.detail.value
          },
          bindSendDanmu: function () {
              this.videoContext.sendDanmu({
                  text: this.inputValue,
                  color: getRandomColor()
              })
          },
          bindPlay: function() {
              this.videoContext.play()
          },
          bindPause: function() {
              this.videoContext.pause()
          },
          videoErrorCallback: function(e) {
              console.log('视频错误信息:')
              console.log(e.detail.errMsg)
          },
          pause: function (e) {
              console.log('pause');
          },
          ended: function (e) {
              console.log('ended');
              // this.next();
          },
          next: function (e) {
              let list = this.srcList;
              let current = (this.current + 1) % list.length;
              this.setData({
                  'src': list[current]
              });
              this.setData({
                  'current': current
              });
          },
          setmuted: function (e) {
              this.setData({
                  'muted': !this.muted
              });
          }
      }
  }
</script>

<style lang="scss">
.video-wrap {
    padding: 60rpx 46rpx 0
}

.btn {
    margin: 30rpx 46rpx 0
}
</style>
