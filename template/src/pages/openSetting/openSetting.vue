<template>
    <div class="container">
        <div class="page-body">
            <button @click="openSetting" type="primary" hover-stop-propagation="true">打开设置</button>
        </div>
        <div class="page-title">
            <div class="page-title-line"></div>
            <div class="page-title-text">\{{title}}</div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "openSetting",
      data() {
        return {
            title: 'openSetting'
        }
      },
      methods: {
          openSetting() {
              duv.openSetting({});
          }
      }
  }
</script>

<style scoped>

</style>
