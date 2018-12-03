<template>
    <div class="wrap">
        <div class="mini-btn-content">
            <div class="title">默认态</div>
            <button type="primary" size="mini" class="mini-btn primary">
                按钮
            </button>
            <button type="default" size="mini" class="mini-btn">按钮</button>
            <button type="warn"    size="mini" class="mini-btn warn">
                按钮
            </button>
        </div>

        <div class="mini-btn-content">
            <div class="title">按下态/无效态</div>
            <button type="primary" size="mini" class="mini-btn primary disabled">
                按钮
            </button>
            <button type="default" size="mini" class="mini-btn disabled">
                按钮
            </button>
            <button type="warn"    size="mini" class="mini-btn warn disabled">
                按钮
            </button>
        </div>

        <div class="btn-content">
            <button type="primary" class="btn primary">
                主操作按钮 默认态
            </button>
            <button type="primary" class="btn primary disabled" disabled>
                主操作按钮 按下/无效态
            </button>
            <button type="default" class="btn">
                次要操作按钮 默认态
            </button>
            <button type="default" class="btn disabled" disabled>
                次要操作按钮 按下/无效态
            </button>
            <button type="warn" class="btn warn">
                警告类操作按钮 默认态
            </button>
            <button type="warn" class="btn warn disabled" disabled>
                警告类操作按钮 按下/无效态
            </button>
        </div>

        <div>
            <button type="default" class="middle-btn" open-type="share">按钮</button>
            <button type="default" class="middle-btn disabled" open-type="share">
                按钮
            </button>

        </div>
    </div>

</template>

<script>
  export default {
    name: "button",
      methods: {
          onShareAppMessage() {
              return {
                  title: '小程序标题',
                  content: '世界很复杂，百度更懂你',
                  imageUrl: 'http://imgsrc.baidu.com/forum/pic/item/d9f9d72a6059252daecdfc36309b033b5bb5b92e.jpg',
                  path: '/pages/openShare/openShare',
                  success(res) {
                      // 分享成功
                  },
                  fail(err) {
                      // 分享失败
                  }
              };
          },
          getUserInfo(e) {
              duv.getUserInfo({
                  success: res => {
                      swan.showModal({
                          title: '获取成功',
                          content: JSON.stringfy(res)
                      });
                  },
                  fail: err => {
                      duv.showToast({
                          title: '获取失败'
                      });
                  }
              });
          }
      }
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
        padding-top: 140rpx;
    }
    .mini-btn-content {
        margin-bottom: 24rpx;
    }
    .title {
        display: inline-block;
        width: 268rpx;
        font-size: 32rpx;
        color: #999;
        padding: 0 0 0 40rpx !important;
    }
    .mini-btn {
        margin: 0 40rpx 0 0  !important;
        padding: 0 !important;
        width: 114rpx;
        height: 56rpx;
        line-height: 56rpx !important;
    }
    .mini-btn:last-child {
        margin-right: 0 !important;
    }
    .btn-content {
        padding-top: 104rpx;
    }
    .btn {
        margin: 0 auto 24rpx !important;
        padding: 0 !important;
        width: 658rpx;
        height: 86rpx;
        line-height: 88rpx;
    }
    .middle-btn {
        margin: 0 auto 30rpx;
        width: 220rpx;
        height: 72rpx;
        line-height: 72rpx;
    }
    .disabled {
        opacity: .3 !important;
    }
    .primary::after,
    .warn::after {
        border: none !important;
    }

</style>
