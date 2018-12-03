<template>
    <div class="wrap">
        <div class="title">设置step</div>
        <slider min="0" max="1500" value="200" step="30" show-value @change="sliderChange"></slider>
        <div class="title">显示当前value</div>
        <slider min="0" max="1500" value="421" show-value @change="sliderChange"></slider>
        <div class="title">设置最小最大值</div>
        <slider min="200" max="1500" value="330" show-value @change="sliderChange"></slider>
    </div>
</template>

<script>
  export default {
    name: "slider",
      methods: {
          sliderChange(e) {
              console.log(e);
          }
      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
    }

</style>
