<template>
    <div>
        <navigator class="nav" url="/pages/detail/main">跳转到新页面</navigator>
        <navigator class="nav" url="/pages/detail/main" open-type="redirect" >在当前页打开</navigator>
    </div>
</template>

<script>
  export default {
    name: "navigator"
  }
</script>

<style>
    .btn {
        margin: 30rpx 46rpx 0;
    }
    .nav {
        display: block;
    }
</style>
