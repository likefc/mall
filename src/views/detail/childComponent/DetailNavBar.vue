<template>
  <div>
    <nav-bar>
      <div slot="left" class="back" @click="backClick">
        <img src="~assets/img/common/back.svg" alt="">
      </div>
      <div slot="center" class='title'>
        <div v-for='(item, index) in titles' :key="index" class="title-item" :class="{active: currentIndex === index}" @click='currentIndex = index'>{{item}}</div>
      </div>
    </nav-bar>
  </div>
</template>
<script>
import NavBar from 'components/common/navbar/NavBar'
export default {
  name: 'DetailNavBar',
  data() {
    return {
      titles: ['商品', '参数', '评论', '推荐'],
      currentIndex: 0
    }
  },
  components: {
    NavBar
  },
  methods: {
    backClick() {
      console.log('1')
      this.$router.back()
    }
  }
}
</script>
<style scoped>
.title {
  display: flex;
}
.title-item {
  flex: 1;
  cursor: pointer;
  text-align: center;
}
.active {
  color: var(--color-high-text);
}
.back img {
  margin-top: 10px;
  margin-left: 10px;
}
</style>
