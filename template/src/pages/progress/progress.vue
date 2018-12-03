<template>
    <div class="wrap">
        <progress class="progress" percent="20" activeColor="#3c76ff" stroke-width="2" show-info />
        <progress class="progress" percent="40" activeColor="#3c76ff" active />
        <progress class="progress" percent="60" activeColor="#3c76ff" active />
        <progress class="progress" percent="80" activeColor="#74fa7d" active />
    </div>

</template>

<script>
  export default {
    name: "progress"
  }
</script>

<style>
    .wrap {
        font-size: 32rpx;
        padding: 60rpx 30rpx;
    }
    .progress {
        margin-bottom: 70rpx;
        border-radius: 3px;
    }

</style>
