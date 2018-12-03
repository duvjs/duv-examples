<template>
    <div class="container">
        <div class="wrap">
            <div class="title">Local Image</div>
            <div class="img-box local-img">
                <img class="swan-icon" src="../../images/local-image.png" />
            </div>
            <div class="title">Internet Image</div>
            <div class="img-box internet-img">
                <img class="swan-icon" src="../../images/internet-image.png" />
            </div>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">image</div>
        </div>
    </div>

</template>

<script>
  export default {
    name: "image"
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
    }
    .img-box {
        margin: auto 46rpx;
        position: relative;
        height: 226rpx;
    }
    .local-img {
        background: #EAEAEA;
    }
    .internet-img {
        background-color: #D2D3D4;
    }
    .swan-icon {
        width: 292rpx;
        height: 54rpx;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

</style>
