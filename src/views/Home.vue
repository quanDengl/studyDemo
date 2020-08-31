<template>
  <div class="home">
    <h2>基本配置完成</h2>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {
    HelloWorld: () => import(/* webpackChunkName: 'PopupApp' */ '@/components/HelloWorld')
  }
}
</script>
<style lang="scss" scoped>
.home {
  h2 {
    text-align: center;
  }
}
</style>