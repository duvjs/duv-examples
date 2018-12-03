<template>
    <audio :poster="poster" :name="name" :author="author" :src="src" id="myAudio" controls @error="error" @play="audioPlay" @pause="audioPause" @timeupdate="timeupdate" @ended="audioEnded"></audio>
</template>

<script>
  export default {
    name: "audio",
      data() {
        return {
            poster: 'http://c.hiphotos.baidu.com/super/pic/item/8b13632762d0f703e34c0f6304fa513d2797c597.jpg',
            name: '演员',
            author: '薛之谦',
            src: 'http://ws.stream.qqmusic.qq.com/M500001VfvsJ21xFqb.mp3?guid=ffffffff82def4af4b12b3cd9337d5e7&uin=346897220&vkey=6292F51E1E384E06DCBDC9AB7C49FD713D632D313AC4858BACB8DDD29067D3C601481D36E62053BF8DFEAF74C0A5CCFADD6471160CAF3E6A&fromtag=46'
        }
      },
      methods: {
          error: function (e) {
              console.log('audio error:', e);
              duv.showToast({
                  title: '加载音频资源出错',
                  duration: 1000
              });
          },
          audioPlay: function (e) {
              console.log('audio play');
              duv.showToast({
                  title: '音频开始播放',
                  duration: 1000
              });
          },
          audioPause: function (e) {
              console.log('audio pause');
              duv.showToast({
                  title: '音频暂停',
                  duration: 1000
              });
          },
          audioEnded: function () {
              console.log('audio ended');
              duv.showToast({
                  title: '音频播放完',
                  duration: 1000
              });
          },
          timeupdate: function () {
              console.log('audio update');
          }
      }
  }
</script>

<style>

</style>
