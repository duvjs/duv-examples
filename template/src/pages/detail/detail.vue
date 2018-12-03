<template>
    <div class="container detail-container">
        <div class="page-body">
        </div>
        <div class="page-title detail-title">
            <div class="page-title-text">\{{title}}</div>
            <div class="page-title-line"></div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "detail",
      data() {
        return {
            title: '新建的页面'
        }
      }
  }
</script>

<style>
    .page-body {
        margin: 84rpx 34rpx 0;
        text-align: center;
        font-size: 36rpx;
    }
    .detail-container {
        background-color: #fff;
    }
    .detail-title {
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
    }
</style>
