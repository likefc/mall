<template>
  <div class="nav-bar">
    <div class="left">
      <slot name="left"></slot>
    </div>
    <div class="center">
      <slot name="center"></slot>
    </div>
    <div class="right">
      <slot name="right"></slot>
    </div>
    <!-- 丰台区 庄维花园8号楼0单元10层1002  -->
  </div>
</template>
<script>
export default {
  name: 'NavBar',
  data() {
    return {}
  },
  components: {}
}
</script>
<style>
.nav-bar {
  display: flex;
  line-height: 44px;
  height: 44px;
  box-shadow: 0 1px 1px rgba(100, 100, 100, 0.1);
  z-index: 100;
}
.left,
.right {
  width: 60px;
}
.center {
  flex: 1;
  text-align: center;
}
</style>
