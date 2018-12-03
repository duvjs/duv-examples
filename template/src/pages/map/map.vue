<template>
    <div class="wrap">
        <div>
            <map
                id="myMap"
                style="width: 100%; height: 300px;"
                :latitude="latitude"
                :longitude="longitude"
                :markers="markers"
                :covers="covers"
                show-location
            ></map>
        </div>
        <div>
            <button @click="getCenterLocation" class="btn" type="primary">获取位置</button>
            <button @click="moveToLocation" class="btn" type="primary">移动位置</button>
            <button @click="translateMarker" class="btn" type="primary">移动标注</button>
            <button @click="includePoints" class="btn" type="primary">缩放视野展示所有经纬度</button>
        </div>
    </div>

</template>

<script>
  export default {
    name: "map",
      data() {
        return {
            mapCtx: null,
            latitude: 23.099994,
            longitude: 113.324520,
            markers: [{
                id: 1,
                latitude: 23.099994,
                longitude: 113.324520,
                name: 'T.I.T 创意园'
            }],
            covers: [{
                latitude: 23.099994,
                longitude: 113.344520,
                iconPath: '../../images/location.png'
            }, {
                latitude: 23.099994,
                longitude: 113.304520,
                iconPath: '../../images/location.png'
            }]
        }
      },
      mounted() {
          this.mapCtx = duv.createMapContext('myMap');
      },
      methods: {
          getCenterLocation: function () {
              this.mapCtx.getCenterLocation({
                  success: function(res){
                      console.log(res.longitude)
                      console.log(res.latitude)
                  },
                  fail: function (err) {
                      console.log(err)
                  }
              })
          },
          moveToLocation: function () {
              this.mapCtx.moveToLocation()
          },
          translateMarker: function() {
              this.mapCtx.translateMarker({
                  markerId: 1,
                  autoRotate: true,
                  duration: 1000,
                  destination: {
                      latitude:23.10229,
                      longitude:113.3345211,
                  },
                  animationEnd() {
                      console.log('animation end')
                  }
              })
          },
          includePoints: function() {
              this.mapCtx.includePoints({
                  padding: [10],
                  points: [{
                      latitude:23.10229,
                      longitude:113.3345211,
                  }, {
                      latitude:23.00229,
                      longitude:113.3345211,
                  }]
              })
          }
      }
  }
</script>

<style>
    .wrap {
        padding: 60rpx 46rpx 0;
    }
    .btn {
        margin: 30rpx 46rpx 0;
    }
</style>
