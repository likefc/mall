<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot name='item-icon'></slot>
    </div>
    <div v-else>
      <slot name='item-icon-active'></slot>
    </div>
    <!-- :class="{'active': isActive}" -->
    <div :style="activeStyle">
      <slot name='item-text'></slot>
    </div>
  </div>
</template>
<script>
export default {
  name: 'TabBarItem',
  data() {
    return {
      // isActive: true
    }
  },
  props: {
    path: String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
  computed: {
    isActive: {
      get() {
        return this.$route.path.indexOf(this.path) > -1
      }
    },
    activeStyle: {
      get() {
        return this.isActive ? { color: this.activeColor } : {}
      }
    }
  },
  methods: {
    itemClick($event) {
      if (this.$route.path === this.path) return
      this.$router.replace(this.path)
    }
  }
}
</script>
<style lang="css">
.tab-bar-item {
  flex: 1;
  text-align: center;
  font-size: 14px;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
}
/* .active {
  color: red;
} */
</style>