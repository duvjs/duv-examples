<template>
    <div class="container">
        <div class="page-body">
            <button @click="startPullDownRefresh" hover-stop-propagation="true">开始下拉刷新</button>
            <button @click="stopPullDownRefresh" hover-stop-propagation="true">停止刷新</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "pullDownRefresh",
      data() {
        return {
            title: 'on/stopPullDownRefresh'
        }
      },
      methods: {
          stopPullDownRefresh() {
              duv.stopPullDownRefresh();
          },
          startPullDownRefresh() {
              duv.startPullDownRefresh()
          }
      }
  }
</script>

<style>
    .page-body {
        margin-top: 0;
    }

    .page-info {
        height: 83px;
        line-height: 83px;
        background-color: #fff;
        color: #000;
        font-size: 18px;
        text-align: center;
    }

    swan-button {
        margin-top: 30rpx;
    }

</style>
