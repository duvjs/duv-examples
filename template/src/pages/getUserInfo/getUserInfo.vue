<template>
    <div class="container">
        <div class="user-content">
            <div class="user-info">
                <img class="avator" :src="imageSrc" />
                <div :class="nameColor + ' nickname'">{{nickname}}</div>
            </div>
            <div class="button-content">
                <button @click="getUserInfo" class="get-info" type="primary" hover-stop-propagation="true">获取用户信息</button>
                <button @click="clearUserInfo" class="clear-info" type="default" hover-stop-propagation="true">清空</button>
            </div>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">{{title}}</div>
        </div>
    </div>

</template>

<script>
  export default {
    name: "getUserInfo",
      data() {
        return {
            nickname: '百度网友',
            imageSrc: '../../images/avator.png',
            nameColor: 'default',
            title: 'getUserInfo'
        }
      },
      methods: {
          getUserInfo(e) {
              duv.getUserInfo({
                  success: res => {
                      let userInfo = res.userInfo;
                      this.setData({
                          nickname: userInfo.nickName || '百度网友',
                          imageSrc: userInfo.avatarUrl || '../../images/avator.png',
                          nameColor: 'active'
                      });
                  },
                  fail: err => {
                      console.log(err);
                      duv.showToast({
                          title: '请先授权'
                      });
                  }
              });
          },
          clearUserInfo(e) {
              this.setData({
                  nickname: '百度网友',
                  imageSrc: '../../images/avator.png',
                  nameColor: 'default'
              });
          }
      }
  }
</script>

<style>
    .user-info {
        padding-top: 200rpx;
    }
    .avator {
        width: 190rpx;
        height: 190rpx;
        margin: 0 auto;
        display: block;
        border-radius: 50%;
    }
    .nickname {
        font-size: 36rpx;
        text-align: center;
        height: 116rpx;
        line-height: 116rpx;
        padding: 0 30rpx;
    }
    .nickname.default {
        color: #999;
    }
    .nickname.active {
        color: #333;
    }
    .button-content {
        position: relative;
        top: 0;
    }
    .button-content button {
        margin-top: 30rpx;
        border-radius: 8rpx;
    }
    .get-info {
        margin-top: 78rpx!important;
    }
    .get-info::after {
        border: none;
    }
    .clear-info::after {
        border-color: #999;
    }
</style>
