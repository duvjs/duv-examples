<template>
    <div class="container">
        <div class="page-body">
            <div class="title">当前位置经纬度</div>
            <div v-if="location" class="info">E: {{location.longitude[0]}}°{{location.longitude[1]}}′ N: {{location.latitude[0]}}°{{location.latitude[1]}}′</div>
            <div v-else class="info">未获取</div>
            <button @click="getLocation" type="primary" :loading="loading" hover-stop-propagation="true">点击获取位置信息</button>
            <button @click="clearLocation" hover-stop-propagation="true">清空</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "getLocation",
      data() {
          return {
              title: 'getLocation',
              loading: false,
              location: ''
          }
      },
      methods: {
          getLocation(e) {
              this.setData({
                  'loading': true
              });
              duv.getLocation({
                  type: 'wgs84',
                  altitude: true,
                  success: res => {
                      this.setData({
                          'location': this.formatLocation(res.longitude, res.latitude)
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '获取失败'
                      });
                  },
                  complete: () => {
                      this.setData({
                          'loading': false
                      });
                  }
              });
          },

          clearLocation(e) {
              this.setData({
                  'location': ''
              });
          },

          formatLocation(longitude, latitude) {
              if (typeof longitude === 'string' && typeof latitude === 'string') {
                  longitude = parseFloat(longitude);
                  latitude = parseFloat(latitude);
              }

              longitude = longitude.toFixed(2);
              latitude = latitude.toFixed(2);

              return {
                  longitude: longitude.toString().split('.'),
                  latitude: latitude.toString().split('.')
              };
          }
      }
  }
</script>

<style>
    .page-body {
        margin-top: 0;
    }

    swan-button {
        margin-top: 30rpx;
    }

    .info {
        height: 83px;
        line-height: 83px;
        background-color: #fff;
        color: #000;
        font-size: 30px;
        text-align: center;
    }

</style>
