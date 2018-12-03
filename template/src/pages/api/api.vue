<template>
    <div class="group">
        <div class="group-hd">
            <img class="group-logo" src="../../images/api_logo.png" />
            <div class="group-desc">以下将演示小程序接口能力，具体属性参数详见小程序开发文档。</div>
        </div>

        <div v-for="(item, index, key) in items" :key="key" class="group-bd">
            <div :class="item.open ? 'item border-bottom ' : 'item border-bottom item-close'" @click="toggleClick" :data-index="index" :data-id="item.id">
                <img class="item-logo" :src="item.icon" />
                <text class="item-desc">\{{item.name}}</text>
                <img v-if="item.id" class="item-logo item-toggle" src="../../images/right_arrow.png" />
                <img v-else class="item-logo item-toggle" :src="item.open ? '../../images/close.png' : '../../images/open.png'" />
            </div>
            <view v-if="item.open">
                <view class="sub-item border-bottom" v-for="(subItem,key) in item.list" :key="key" @click="oneItemClick" :data-id="subItem.id">
                    <text class="sub-item-desc">\{{subItem.subName}}</text>
                    <img class="item-logo sub-item-goto" src="../../images/right_arrow.png" />
                </view>
            </view>
        </div>
    </div>
</template>

<script>
  export default {
    name: "api",
      data() {
        return {
            items: [{
                icon: '../../images/interface.png',
                name: '开放接口',
                open: false,
                list: [{
                    subName: '授权',
                    id: 'authorize'
                }, {
                    subName: '获取用户信息',
                    id: 'getUserInfo'
                }, {
                    subName: '登录',
                    id: 'login'
                }, {
                    subName: '支付',
                    id: 'payment'
                }, {
                    subName: '设置',
                    id: 'openSetting'
                }, {
                    subName: '分享',
                    id: 'openShare'
                }]
            }, {
                icon: '../../images/ui.png',
                name: '界面',
                open: false,
                list: [{
                    subName: '设置页面标题',
                    id: 'setNavigationBarTitle'
                }, {
                    subName: '标题栏加载动画',
                    id: 'navigationBarLoading'
                }, {
                    subName: '页面跳转',
                    id: 'navigateTo'
                }, {
                    subName: '下拉刷新',
                    id: 'pullDownRefresh'
                }, {
                    subName: '显示操作菜单',
                    id: 'showActionSheet'
                }, {
                    subName: '显示模态弹窗',
                    id: 'modal'
                }, {
                    subName: '显示消息提示框',
                    id: 'toast'
                }]
            }, {
                icon: '../../images/device.png',
                name: '设备',
                open: false,
                list: [{
                    subName: '获取手机系统信息',
                    id: 'getSystemInfo'
                }, {
                    subName: '获取手机网络状态',
                    id: 'getNetworkType'
                }, {
                    subName: '监听手机网络状态',
                    id: 'onNetworkStatusChange'
                }, {
                    subName: '监听重力感应数据',
                    id: 'getGravity'
                }, {
                    subName: '监听罗盘数据',
                    id: 'getCompass'
                }, {
                    subName: '拨打电话',
                    id: 'makePhoneCall'
                }, {
                    subName: '剪贴板',
                    id: 'clipboardData'
                }]
            }, {
                icon: '../../images/net.png',
                name: '网络',
                open: false,
                list: [{
                    subName: '发起请求',
                    id: 'request'
                }, {
                    subName: '上传文件',
                    id: 'uploadFile'
                }, {
                    subName: '下载文件',
                    id: 'downloadFile'
                }]
            }, {
                icon: '../../images/media.png',
                name: '媒体',
                open: false,
                list: [{
                    subName: '图片',
                    id: 'api-image'
                }, {
                    subName: '文件',
                    id: 'file'
                }, {
                    subName: '选择视频',
                    id: 'chooseVideo'
                    // }, {
                    //     subName: '录音管理',
                    //     id: 'getRecorderManager'
                }]
            }, {
                icon: '../../images/location.png',
                name: '位置',
                open: false,
                id: 'getLocation'
            }, {
                icon: '../../images/storage.png',
                name: '数据',
                id: 'storage',
                open: false
            }]
        }
      },
      methods: {
          toggleClick(e) {
              // 无子项直接跳转
              let apiName = e.currentTarget.dataset.id;
              if (apiName) {
                  duv.navigateTo({
                      url: '/pages/' + apiName + '/main'
                  });
                  return;
              }
              // 子项展开与收起
              let items = this.items;
              let index = e.currentTarget.dataset.index;
              items[index].open = !items[index].open;
              this.setData({
                  'items': items
              });
          },

          oneItemClick(e) {
              let apiName = e.currentTarget.dataset.id;
              duv.navigateTo({
                  url: '/pages/' + apiName + '/main'
              });
          }
      }
  }
</script>

<style>
    .group {
        font-size: 30rpx;
    }

    .group-hd {
        height: 374rpx;
        padding: 0 44rpx 0 58rpx;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #fff;
    }

    .group-logo {
        width: 104rpx;
        height: 104rpx;
    }

    .item-logo {
        width: 52rpx;
        height: 52rpx;
    }

    .group-desc {
        text-align: center;
        color: #999;
        margin-top: 28rpx;
        line-height: 1.6;
    }

    .group-bd {
        border-top: 7px solid #f5f5f5;
        background: #fff;
    }

    .group-bd:last-child {
        border-bottom: 7px solid #f5f5f5;
    }

    .item {
        padding: 34rpx 46rpx 34rpx 60rpx;
        position: relative;
        display: flex;
        align-items: center;
    }

    .item-close:after {
        height: 0;
    }

    .item-logo {
        display: inline-block;
    }

    .item-desc {
        font-size: 34rpx;
        margin-left: 36rpx;
    }

    .item-toggle {
        position: absolute;
        right: 46rpx;
    }

    .sub-item {
        position: relative;
        margin-left: 150rpx;
        padding: 25rpx 0;
        display: flex;
        align-items: center;
    }

    .sub-item:last-child:after {
        height: 0;
    }

    .sub-item-goto {
        position: absolute;
        right: 46rpx;
    }

    .sub-item-desc {
        color: #666;
    }
</style>
