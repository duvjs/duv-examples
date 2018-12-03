<template>
    <div class="wrap">
        <div class="title">默认样式</div>
        <radio-group @change="radioChange" class="radio-group">
            <radio class="radio" checked>&nbsp;&nbsp;选中</radio>
            <radio class="radio" checked="false">&nbsp;&nbsp;未选中</radio>
        </radio-group>

        <div class="title">推荐示例</div>
        <div class="item-wrap">
            <radio-group @change="radioChange">
                <label v-for="(item,key) in items" :key="key" class="radio-background-active" :for="item.id">
                    <div class="item">
                        <radio :value="item.value" :checked="item.checked" :id="item.id">&nbsp;&nbsp;\{{item.text}}</radio>
                    </div>
                </label>
            </radio-group>
        </div>
    </div>
</template>

<script>
  export default {
    name: "radio",
      data() {
        return {
            items: [
                {
                    value: 'have',
                    text: '选中选项',
                    checked: true,
                    id: 1
                },
                {
                    value: 'have',
                    text: '未选中选项',
                    id: 2
                },
                {
                    value: 'none',
                    text: '未选中选项',
                    id: 3
                }
            ],
            result: []
        }
      },
      methods: {
          radioChange: e => {
              console.log(e);
          },

          formSubmit: e => {
              console.log('ljh', e);
          }
      }
  }
</script>

<style>

    .wrap {
        font-size: 32rpx;
    }

    .radio {
        margin: 0 50rpx;
    }
    .item-wrap {
        background: #fff;
    }
    .item {
        padding: 30rpx 0;
        border-bottom: 1px #f5f5f5 solid;
        margin-left: 50rpx;
    }
    .radio-background-active:active {
        display: block;
        background-color: #f2f2f2;
    }
    .switch {
        float: right;
    }

</style>
