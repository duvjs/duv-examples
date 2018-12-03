<template>
    <div class="wrap">
        <div class="title">默认样式</div>
        <div>
            <switch class="init-switch" checked></switch><text class="switch-text">开启</text>
            <switch class="init-switch"></switch><text class="switch-text">关闭</text>
        </div>

        <div class="title">推荐示例</div>
        <div class="item-wrap">
            <div class="item">
                <span>开启选项</span>
                <switch checked class="switch"></switch>
            </div>
            <div class="item">
                <span>关闭选项</span>
                <switch class="switch"></switch>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "switch"
  }
</script>

<style>

    .wrap {
        font-size: 32rpx;
    }
    .init-switch {
        margin: 0 10rpx 0 50rpx;
        vertical-align: middle;

    }
    .switch-text {
        vertical-align: -4rpx;
    }
    .item-wrap {
        background: #fff;
    }
    .item {
        padding: 30rpx 0;
        border-bottom: 1px #f5f5f5 solid;
        margin-left: 40rpx;
        position: relative;
    }
    .switch {
        position: absolute;
        top: 50%;
        right: 40rpx;
        transform: translateY(-50%);
    }

</style>
