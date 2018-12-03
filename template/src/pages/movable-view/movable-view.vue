<template>
    <div class="page-body">
        <div class="page-section">
            <div class="page-section-title">movable-view区域小于movable-area</div>
            <movable-area class="movable-area">
                <movable-view class="movable-view" :x="x" :y="y" direction="all">text</movable-view>
            </movable-area>
        </div>
        <div class="btn-area">
            <button @click="tap" class="page-body-button" type="primary">click me to move to (30px, 30px)</button>
        </div>

        <div class="page-section">
            <div class="page-section-title">movable-view区域大于movable-area</div>
            <movable-area class="movable-area">
                <movable-view class="max movable-view" direction="all">text</movable-view>
            </movable-area>
        </div>

        <div class="page-section">
            <div class="page-section-title">只可以横向移动</div>
            <movable-area class="movable-area">
                <movable-view class="movable-view" direction="horizontal">text</movable-view>
            </movable-area>
        </div>

        <div class="page-section">
            <div class="page-section-title">只可以纵向移动</div>
            <movable-area class="movable-area">
                <movable-view class="movable-view" direction="vertical">text</movable-view>
            </movable-area>
        </div>

        <div class="page-section">
            <div class="page-section-title">可超出边界</div>
            <movable-area class="movable-area">
                <movable-view class="movable-view" direction="all" out-of-bounds>text</movable-view>
            </movable-area>
        </div>

        <div class="page-section">
            <div class="page-section-title">带有惯性</div>
            <movable-area class="movable-area">
                <movable-view class="movable-view" direction="all" inertia>text</movable-view>
            </movable-area>
        </div>

        <div class="page-section">
            <div class="page-section-title">可放缩</div>
            <movable-area  class="movable-area" scale-area>
                <movable-view class="movable-view" direction="all" @change="onChange" @scale="onScale" scale scale-min="0.5" scale-max="4" :scale-value="scale">text</movable-view>
            </movable-area>
        </div>

        <div class="btn-area">
            <button @click="tap2" class="page-body-button" type="primary">click me to scale to 3.0</button>
        </div>
    </div>
</template>

<script>
  export default {
    name: "movable-view",
      data() {
        return {
            x: 0,
            y: 0,
            scale: 2,
        }
      },
      methods: {
          tap(e) {
              this.setData({
                  x: 30,
                  y: 30
              })
          },
          tap2() {
              this.setData({
                  scale: 3
              })
          },
          onChange(e) {
              console.log(e.detail)
          },
          onScale(e) {
              console.log(e.detail)
          }
      }
  }
</script>

<style>
.movable-view {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100rpx;
    width: 100rpx;
    background: #1AAD19;
    color: #fff;
}

.movable-area {
    height: 400rpx;
    width: 400rpx;
    margin: 50rpx;
    background-color: #ccc;
    overflow: hidden;
}

.max {
    width: 600rpx;
    height: 600rpx;
}

.page-section{
    width: 100%;
    margin-bottom: 60rpx;
}

.page-section:last-child{
    margin-bottom: 0;
}

.page-section-title{
    font-size: 28rpx;
    color: #999999;
    margin-bottom: 10rpx;
    padding-left: 30rpx;
    padding-right: 30rpx;
}

</style>
