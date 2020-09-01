<template>
  <div class="home">
    <h2>基本配置完成</h2>
    <slide-grid></slide-grid>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {
    HelloWorld: () => import(/* webpackChunkName: 'PopupApp' */ '@/components/HelloWorld'),
    SlideGrid: () => import(/* webpackChunkName: 'PopupApp' */ '@/components/SlideGrid')
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