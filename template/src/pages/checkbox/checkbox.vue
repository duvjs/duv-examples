<template>
    <div class="wrap">
        <div class="title">默认样式</div>
        <checkbox-group @change="radioChange" class="checkbox-group">
            <checkbox class="checkbox" checked>&nbsp;&nbsp;选中</checkbox>
            <checkbox class="checkbox" checked="false">&nbsp;&nbsp;未选中</checkbox>
        </checkbox-group>

        <div class="title">推荐示例</div>
        <div class="item-wrap">
            <form>
                <div class="checkbox-content" v-for="(item,key) in items" :key="key">
                    <label class="checkbox-background-active" :for="item.id">
                        <div class="item">
                            <checkbox class="takeplace" :value="item.value" :checked="item.checked" :id="item.id">11</checkbox>
                        </div>
                    </label>
                    <div class="checkbox-item">
                        <checkbox :value="item.value" :checked="item.checked" :id="item.id">&nbsp;&nbsp;{{item.text}}</checkbox>
                    </div>
                </div>
            </form>
        </div>
    </div>

</template>

<script>
  export default {
    name: "checkbox",
      data() {
        return {
            items: [
                {
                    value: 'China',
                    text: '中国',
                    id: '1'
                },
                {
                    value: 'US',
                    text: '美国',
                    id: '2'
                },
                {
                    value: 'Britain',
                    text: '英国',
                    checked: true,
                    id: '3'
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
    .checkbox {
        margin: 0 40rpx;
    }
    .item-wrap {
        background: #fff;
    }
    .checkbox-content {
        position: relative;
    }
    .item {
        padding: 30rpx 0;
        border-bottom: 1px #f5f5f5 solid;
        margin-left: 40rpx;
    }
    .checkbox-item {
        padding: 30rpx 0;
        position: absolute;
        top: 0;
        left: 40rpx;
    }
    .checkbox-background-active:active {
        display: block;
        background-color: #f2f2f2;
    }
    .switch {
        float: right;
    }
    .takeplace {
        visibility: hidden;
    }

</style>
