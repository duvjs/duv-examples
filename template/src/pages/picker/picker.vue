<template>
    <div class="wrap">
        <div class="title">时间选择</div>
        <form>
            <label class="section" for="section1">
                <div class="section-title">当前选择</div>
                <picker id="section1" mode="time" :value="time" start="1:01" end="22:59" @change="timeChange">
                    <div class="picker">
                        \{{time}}
                    </div>
                </picker>
            </label>
        </form>
        <div class="title">日期选择</div>
        <form>
            <label class="section date-section" for="section2">
                <div class="section-title">当前选择</div>
                <picker id="section2" mode="date" :value="dateDay" @change="dateChangeDay" fields="day">
                    <div>
                        \{{dateDay}}
                    </div>
                </picker>
            </label>
        </form>
        <form>
            <label class="section date-section" for="section3">
                <div class="section-title">当前选择</div>
                <picker id="section3" mode="date" :value="dateMonth" @change="dateChangeMonth" fields="month">
                    <div>
                        \{{dateMonth}}
                    </div>
                </picker>
            </label>
        </form>
        <form>
            <label class="section date-section" for="section4">
                <div class="section-title">当前选择</div>
                <picker id="section4" mode="date" :value="dateYear" @change="dateChangeYear" fields="year">
                    <div>
                        \{{dateYear}}
                    </div>
                </picker>
            </label>
        </form>
        <div class="title">地区选择</div>
        <form>
            <label class="section" for="section5">
                <div class="section-title">当前选择</div>
                <picker id="section5" mode="region" @change="regionChange" :custom-item="customItem" title="地区选择器">
                    <div class="picker">
                        \{{regionData[0]}} \{{regionData[1]}} \{{regionData[2]}}
                    </div>
                </picker>
            </label>
        </form>
    </div>
</template>

<script>
  export default {
    name: "picker",
      data() {
        return {
            time: '12:12',
            dateDay: '2018-01-05',
            dateMonth: '2018-01',
            dateYear: '2018',
            regionData: ['全部', '全部', '全部'],
            customItem: '全部'
        }
      },
      methods: {
          timeChange(e) {
              console.log('picker-time changed，值为', e.detail.value);
              this.setData({
                  'time': e.detail.value
              });
          },
          dateChangeDay(e) {
              console.log('picker-date changed，值为', e.detail.value);
              this.setData({
                  'dateDay': e.detail.value
                  });
          },
          dateChangeMonth(e) {
              console.log('picker-date changed，值为', e.detail.value);
              this.setData({
                  'dateMonth': e.detail.value
              });
          },
          dateChangeYear(e) {
              console.log('picker-date changed，值为', e.detail.value);
              this.setData({
                  'dateYear': e.detail.value
                  });
          },
          regionChange(e) {
              this.setData({
                      'regionData': e.detail.value
                  });
              console.log('picker-time changed，值为', e.detail.value);
          }
      }
  }
</script>

<style>

    .wrap {
        font-size: 32rpx;
    }
    .date-section {
        margin-bottom: 20rpx;
    }
    .section {
        height: 120rpx;
        line-height: 120rpx;
        font-size: 36rpx;
        background: #fff;
        padding: 0 44rpx;
        display: flex;
    }
    .section:active {
        background-color: #f2f2f2;
    }
    .section-title {
        color: #000;
        flex: 0 0 200rpx;
    }

</style>
