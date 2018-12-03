<template>
    <div>
        <div class="section">
            <div class="title">可以自动聚焦的input</div>
            <input class="ipt" placeholder="将会获取焦点" focus="autoFocus"/>
        </div>

        <div class="section">
            <div class="title">控制最大输入长度的input</div>
            <input class="ipt" maxlength="10" placeholder="最大输入长度为10" />
        </div>
        <div class="section">
            <div class="title">实时获取输入值：{{inputValue}}</div>
            <input class="ipt" @input="bindKeyInput" placeholder="输入同步到view中" maxlength="19"/>
        </div>

        <div class="section">
            <div class="title">数字输入的input</div>
            <input class="ipt" type="number" placeholder="这是一个数字输入框" />
        </div>
        <div class="section">
            <div class="title">密码输入的input</div>
            <input class="ipt" password placeholder="这是一个密码输入框" />
        </div>
        <div class="section">
            <div class="title">带小数点的input</div>
            <input class="ipt" type="digit" placeholder="带小数点的数字键盘"/>
        </div>
        <div class="section">
            <div class="title">身份证输入的input</div>
            <input class="ipt" type="idcard" placeholder="身份证输入键盘" />
        </div>
        <div class="section" style="padding-bottom: .2rem;">
            <div class="title">控制占位符颜色的input</div>
            <input class="ipt" placeholder-style="color:red" placeholder="占位符字体是红色的" />
        </div>
    </div>
</template>

<script>
  export default {
    name: "input",
      data() {
        return {
            focus: false,
            inputValue: '',
            autoFocus: true
        }
      },
      methods: {
          bindButtonTap: function () {
              this.setData({
                  focus: true
              });
          },
          bindKeyInput: function (e) {
              this.setData({
                  inputValue: e.detail.value
              });
          }
      }
  }
</script>

<style>

    .section {
        font-size: 32rpx;
    }
    .title {
        padding: 40rpx 40rpx 28rpx !important;
    }
    .ipt {
        /*margin: 0 .2rem .07rem .2rem;*/
        width: 100%;
        padding-left: 40rpx;
        height: 80rpx;
        background: #fff;
    }
    .small-ipt {
        width: 558rpx;
    }

</style>
