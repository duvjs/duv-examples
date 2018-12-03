<template>
    <div>hello world</div>
</template>
<script type="es6">
export default {
    data() {
        return {
            name: 'xuchaozheng'
        }
    },
    config: {
        "pages":[
            "pages/component/main",
            "pages/view/main",
            "pages/icon/main",
            "pages/text/main",
            "pages/scroll-view/main",
            "pages/swiper/main",
            "pages/progress/main",
            "pages/button/main",
            "pages/checkbox/main",
            "pages/input/main",
            "pages/label/main",
            "pages/picker/main",
            "pages/radio/main",
            "pages/slider/main",
            "pages/switch/main",
            "pages/navigator/main",
            "pages/detail/main",
            "pages/audio/main",
            "pages/image/main",
            "pages/video/main",
            "pages/canvas/main",
            "pages/map/main",
            "pages/movable-view/main",
            "pages/cover-view/main",
            "pages/rich-text/main",
            "pages/web-view/main",
            "pages/api/main",
            // 接口
            "pages/authorize/main",
            "pages/getUserInfo/main",
            "pages/login/main",
            "pages/payment/main",
            "pages/openSetting/main",
            "pages/openShare/main",
            "pages/setNavigationBarTitle/main",
            "pages/navigationBarLoading/main",
            "pages/navigateTo/main",
            "pages/pullDownRefresh/main",
            "pages/showActionSheet/main",
            "pages/modal/main",
            "pages/toast/main",
            "pages/getSystemInfo/main",
            "pages/getNetworkType/main",
            "pages/onNetworkStatusChange/main",
            "pages/getGravity/main",
            "pages/getCompass/main",
            "pages/makePhoneCall/main",
            "pages/clipboardData/main",
            "pages/api-image/main",
            "pages/storage/main",
            "pages/getLocation/main",
            "pages/chooseVideo/main",
            "pages/file/main",
            "pages/request/main",
            "pages/uploadFile/main",
        ],
        "window":{
            "backgroundTextStyle":"light",
            "navigationBarBackgroundColor": "#fff",
            "navigationBarTitleText": "duv组件",
            "navigationBarTextStyle":"black"
        },
        "tabBar": {
            "color": "#a2a2a2",
            "selectedColor": "#3388ff",
            "borderStyle": "black",
            "backgroundColor": "#ffffff",
            "list": [{
                "pagePath": "pages/component/main",
                "iconPath": "images/component_normal.png",
                "selectedIconPath": "images/component_selected.png",
                "text": "组件"
            }, {
                "pagePath": "pages/api/main",
                "iconPath": "images/API_normal.png",
                "selectedIconPath": "images/API_selected.png",
                "text": "接口"
            }]
        }
    }
}
</script>
<style lang="scss">
/*@import "common/base.css";*/
/** {*/
    /*margin: 0;*/
    /*padding: 0;*/
    /*box-sizing: border-box;*/
/*}*/
/*html,*/
/*body {*/
    /*background-color: #f5f5f5;*/
    /*font-size: 100px;*/
    /*font-family: -apple-system-font, Helvetica Neue, Helvetica, sans-serif;*/
    /*height: 100%;*/
/*}*/
/*@media screen and (max-width: 360px) {*/
    /*html {*/
        /*font-size: 90px;*/
    /*}*/
/*}*/
swan-wrapper {
    height: 100%;
}

swan-button {
    margin: 0 46rpx;
}

.container {
    display: flex;
    flex-direction: column;
    min-height: 100%;
    justify-content: space-between;
    font-size: 32rpx;
}

.ensp {
    white-space: normal;
}

.page-body {
    margin-top: 84rpx;
}

.title {
    font-size: 30rpx;
    color: #666;
    padding: 60rpx 44rpx 36rpx 44rpx;
}

.input {
    box-sizing: content-box;
    margin: 0 22.67px 30rpx;
    height: 76rpx;
    line-height: 76rpx;
    font-size: 36rpx;
    padding-left: 20rpx;
}

.page-title {
    margin: 200rpx 0 60rpx 0;
    text-align: center;
}

.page-title-line {
    margin: 0 auto;
    width: 166rpx;
    height: 4rpx;
    background-color: #E6E6E6;
}
.page-top {
    text-align: center;
    margin-top: 72rpx;
}
.page-top-line {
    margin: 0 auto;
    width: 108rpx;
    height: 20rpx;
    background-color: #979797;
    border: 0;
    position: relative;
}
.page-top-text {
    margin-bottom: 20rpx;
    color: #999;
}
.page-title-text {
    margin-top: 14rpx;
    color: #ccc;
}

.border-top {
    border: 0;
    position: relative;
}

.border-top:before {
    content: "";
    position: absolute;
    width: 100%;
    height: 1px;
    left: 0;
    top: 0;
    -webkit-transform-origin: 0 0;
    transform-origin: 0 0;
    background: #e6e6e6;
}

.border-right {
    position: relative;
}

.border-right:after {
    content: "";
    width: 1px;
    position: absolute;
    right: 0;
    top: 0;
    bottom: 0;
    -webkit-transform-origin: 100% 0;
    transform-origin: 100% 0;
    background: #e6e6e6;
}

.border-bottom {
    border: 0;
    position: relative;
}

.border-bottom:after {
    content: "";
    position: absolute;
    width: 100%;
    height: 1px;
    left: 0;
    bottom: 0;
    -webkit-transform-origin: 0 100%;
    transform-origin: 0 100%;
    background: #e6e6e6;
}

.border-left {
    border: 0;
    position: relative;
}

.border-left:before {
    content: "";
    position: absolute;
    height: 100%;
    width: 1px;
    left: 0;
    top: 0;
    -webkit-transform-origin: left center;
    transform-origin: left center;
    background: #e6e6e6;
}

.border-all {
    border: 0;
    position: relative;
}

.border-all:before {
    content: "";
    box-sizing: border-box;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    font-size: 0;
    line-height: 0;
    border-radius: 0;
    border: 1px solid #e6e6e6;
    -webkit-transform-origin: 0 0;
    transform-origin: 0 0;
    background: 0 0;
}

@media only screen and (-webkit-min-device-pixel-ratio: 1.5),
not all {
    .border-top:before,
    .border-bottom:after {
        -webkit-transform: scaleY(0.66666667);
        transform: scaleY(0.66666667);
    }

    .border-right:after,
    .border-left:before {
        -webkit-transform: scaleX(0.66666667);
        transform: scaleX(0.66666667);
    }

    .border-all:before {
        width: 150%;
        height: 150%;
        -webkit-transform: scale(0.66666667);
        transform: scale(0.66666667);
    }
}

@media only screen and (-webkit-min-device-pixel-ratio: 2),
not all {
    .border-top:before,
    .border-bottom:after {
        -webkit-transform: scaleY(0.5);
        transform: scaleY(0.5);
    }

    .border-right:after,
    .border-left:before {
        -webkit-transform: scaleX(0.5);
        transform: scaleX(0.5);
    }

    .border-all:before {
        width: 200%;
        height: 200%;
        -webkit-transform: scale(0.48);
        transform: scale(0.48);
    }
}

@media only screen and (-webkit-min-device-pixel-ratio: 3),
not all {
    .border-top:before,
    .border-bottom:after {
        -webkit-transform: scaleY(0.33333333);
        transform: scaleY(0.33333333);
    }

    .border-right:after,
    .border-left:before {
        -webkit-transform: scaleX(0.33333333);
        transform: scaleX(0.33333333);
    }

    .border-all:before {
        width: 300%;
        height: 300%;
        -webkit-transform: scale(0.3326);
        transform: scale(0.3326);
    }
}
</style>
