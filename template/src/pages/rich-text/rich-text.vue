<template>
    <div class="page-body">
        <div class="page-section">
            <div class="page-section-title">传入html字符串</div>
            <div class="rich-text-wrp">
                <rich-text :nodes="html" @click="tap"></rich-text>
            </div>
        </div>

        <div class="page-section">
            <div class="page-section-title">传入节点列表</div>
            <div class="rich-text-wrp">
                <rich-text :nodes="nodes" @click="tap"></rich-text>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "rich-text",
      data() {
        return {
            html: '<div class="div_class" style="line-height: 60px; color: red;">Hello&nbsp;World!</div>',
            nodes: [{
                name: 'div',
                attrs: {
                    class: 'div_class',
                    style: 'line-height: 60px; color: red;'
                },
                children: [{
                    type: 'text',
                    text: 'Hello&nbsp;World!'
                }]
            }]
        }
      },
      methods: {
          tap() {
              console.log('tap')
          }
      }
  }
</script>

<style>
    rich-text {
        width: 700rpx;
        padding: 25rpx 0;
    }

    .rich-text-wrp {
        padding: 0 25rpx;
        background-color: #fff;
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
