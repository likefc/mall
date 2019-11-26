<template>
  <div class="home-recommend">
    <div
      v-for="(item, index) in recommends"
      :key="index"
      class="recommend-item"
    >
      <a :href="item.link">
        <img :src="item.image" alt="" />
        <div>{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>
<script>
export default {
  name: "HomeRecommend",
  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  components: {}
};
</script>
<style scoped>
.home-recommend {
  display: flex;
  font-size: 12px;
  padding: 10px 0 20px 0;
  border-bottom: solid 10px #eee;
}
.recommend-item {
  flex: 1;
  text-align: center;
}
.recommend-item img {
  width: 80px;
  height: 80px;
}
</style>
