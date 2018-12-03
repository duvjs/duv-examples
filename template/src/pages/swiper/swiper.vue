<template>
    <div class="wrap">
        <div class="title">示例</div>
        <div class="swiper-wrap">
            <swiper
                indicator-color="rgba(0,0,0,0.30)"
                indicator-active-color="#fff"
                :duration="switchDuration"
                :interval="autoPlayInterval"
                :autoplay="switchAutoPlayStatus"
                :indicator-dots="switchIndicateStatus"
                :vertical="false"
                circular="true"
                current="0"
                @change="swiperChange"
            >
                <block v-for="(item,key) in items" :key="key">
                    <swiper-item :class="item.className">
                        <div class="item">\{{item.value}}</div>
                    </swiper-item>
                </block>
            </swiper>
        </div>

        <div class="switch-wrap">
            <div>
                <label>指示器</label>
                <switch :checked="switchIndicateStatus" @change="switchIndicate" class="switch"></switch>
            </div>
            <div>
                <label>自动播放</label>
                <switch :checked="switchAutoPlayStatus" @change="switchAutoPlay" class="switch"></switch>
            </div>
        </div>

        <div class="slider-wrap">
            <div>
                <div class="slider-title-time">
                    <label class="slider-title">幻灯片切换时长</label>
                    <label class="slider-time">\{{switchDuration}}ms</label>
                </div>
                <slider min="300" max="1500" :value="switchDuration"  @change="changeSwitchDuration"></slider>
            </div>

            <div>
                <div class="slider-title-time">
                    <label class="slider-title">自动播放间隔时长</label>
                    <label class="slider-time">\{{autoPlayInterval}}ms</label>
                </div>
                <slider min="1000" max="5000" :value="autoPlayInterval" @change="changeAutoPlayInterval"></slider>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "swiper",
      data() {
        return {
            items: [
                {
                    className: 'color-a',
                    value: 'A'
                }, {
                    className: 'color-b',
                    value: 'B'
                }, {
                    className: 'color-c',
                    value: 'C'
                }
            ],
            imgUrls: [
                'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
                'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
                'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg',
                'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg'
            ],
            current: 0,
            switchIndicateStatus: true,
            switchAutoPlayStatus: false,
            switchDuration: 500,
            autoPlayInterval: 2000
        }
      },
      methods: {
        swiperChange(e) {
              console.log('swiperChange:', e.detail);
          },
          switchIndicate() {
              this.setData({
                  switchIndicateStatus: !this.switchIndicateStatus
              });
          },
          switchAutoPlay() {
              this.setData({
                  switchAutoPlayStatus: !this.switchAutoPlayStatus
              });
          },
          changeSwitchDuration(e) {
              this.setData({
                  switchDuration: e.detail.value
              });
          },
          changeAutoPlayInterval(e) {
              this.setData({
                  autoPlayInterval: e.detail.value
              });
          }

      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
    }
    .swiper-wrap {
        width: 88%;
        margin: 20rpx auto;
    }
    .item {
        width: 100%;
        height: 150px;
        font-size: 32rpx;
        color: #fff;
        text-align: center;
        line-height: 150px;
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

    .switch-wrap {
        padding: 0 34rpx;
        background: #fff;
        margin: 40rpx 0;
    }
    .switch-wrap > view {
        height: 96rpx;
        line-height: 96rpx;
        color: #000;
        font-size: 36rpx;
        border-bottom: 1px #f5f5f5 solid;
        position: relative;
    }
    .switch {
        position: absolute;
        top: 50%;
        right: 0;
        transform: translateY(-50%);
    }
    .slider-wrap > view {
        height: 100%;
        padding: 0 34rpx;
    }
    .slider-title-time {
        overflow: hidden;
        padding: 40rpx 0 20rpx;
    }
    .slider-title,
    .slider-time {
        font-size: 32rpx;
        color: #666;
        line-height: 50rpx;
    }
    .slider-title {
        float: left;
    }
    .slider-time {
        float: right;
        margin-right: 20rpx;
    }

</style>
