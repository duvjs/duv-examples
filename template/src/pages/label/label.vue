<template>
    <div class="wrap">
        <div class="page-section">
            <div class="page-section-title">表单组件在label内</div>
            <checkbox-group class="group">
                <div :class="index === 0 ? 'label-1 label-first': 'label-1'" v-for="(item, index, key) in checkboxItems" :key="key">
                    <label>
                        <checkbox :value="item.name" :checked="item.checked"></checkbox>
                        <span class="label-1-text">\{{item.value}}</span>
                    </label>
                </div>
            </checkbox-group>
        </div>
        <div class="page-section">
            <div class="page-section-title">label用for标识表单组件</div>
            <radio-group class="group">
                <div :class="index === 0 ? 'label-2 label-first': 'label-2'" v-for="(item, index, key) in radioItems" :key="key">
                    <radio :id="item.name" :value="item.name" :checked="item.checked"></radio>
                    <label class="label-2-text" :for="item.name"><span>\{{item.value}}</span></label>
                </div>
            </radio-group>
        </div>
        <div class="page-section">
            <div class="page-section-title">label内有多个时选中第一个</div>
            <label class="label-3">
                <div class="label-box">
                    <div class="checkbox-3 label-first">
                        <checkbox >选项一</checkbox>
                    </div>
                    <div class="checkbox-3">
                        <checkbox>选项二</checkbox>
                    </div>
                </div>
                <div class="label-3-text">点击该label下的文字默认选中第一个checkbox</div>
            </label>
        </div>
    </div>

</template>

<script>
  export default {
    name: "label",
      data() {
        return {
            checkboxItems: [
                {name: 'CHN', value: '中国', checked: 'true'},
                {name: 'USA', value: '美国'}
            ],
            radioItems: [
                {name: 'CHN', value: '中国', checked: 'true'},
                {name: 'USA', value: '美国'}
            ]
        }
      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
    }
    .page-section {
        padding-top: 60rpx;
    }
    .page-section-title {
        padding-bottom: 26rpx;
        padding-left: 34rpx;
        color: #999;
    }
    .group {
        display: block;
        background-color: #fff;
    }
    .label-box {
        display: block;
        background-color: #fff;
    }
    .label-1 {
        margin: 0 34rpx;
        padding: 28rpx 0;
    }
    .label-2 {
        margin: 0 34rpx;
        padding: 28rpx 0;
    }

    .checkbox-3 {
        margin: 0 34rpx;
        padding: 28rpx 0;
    }
    .label-first {
        position: relative;
    }
    .label-3-text {
        padding-top: 26rpx;
        padding-left: 34rpx;
        color: #3E5B9F;
    }
    .label-first:before {
        content: "";
        pointer-events: none;
        box-sizing: border-box;
        position: absolute;
        width: 200%;
        height: 200%;
        left: 0;
        top: 0;
        border-bottom: 1px solid #e6e6e6;
        transform: scale(0.5);
        transform-origin: 0 0;
    }

</style>
