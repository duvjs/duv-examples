<template>
    <div>
        <div>
            <div class="title">横向布局</div>
            <div class="rowlike">
                <div class="color-a">
                    <span>A</span>
                </div>
                <div class="color-b">
                    <span>B</span>
                </div>
                <div class="color-c">
                    <span>C</span>
                </div>
            </div>
        </div>

        <div>
            <div class="title">纵向布局</div>
            <div class="collike">
                <div class="color-a">
                    <span>A</span>
                </div>
                <div class="color-b">
                    <span>B</span>
                </div>
                <div class="color-c">
                    <span>C</span>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
  export default {
    name: "view"
  }
</script>

<style>
    .rowlike {
        width: 90%;
        margin: 0 auto;
        display: flex;
        height: 300rpx;
        line-height: 300rpx;
    }

    .view-title {
        display: block;
        margin: 50rpx 36rpx 36rpx;
        color: #666;
    }

    .rowlike view {
        flex: 1;
        text-align: center;
        font-size: 32rpx;
        color: #FFF;
    }

    .collike {
        margin: 0 auto;
        flex-direction: column;
        width: 480rpx;
    }

    .collike view {
        height: 240rpx;
        line-height: 240rpx;
        flex: 1;
        text-align: center;
        font-size: 32rpx;
        color: #FFF;
    }
    .color-a {
        background-color: #6895FF;
    }
    .color-b {
        background-color: #8FB1FF;
    }
    .color-c {
        background-color: #C3D1FF;
    }

</style>
