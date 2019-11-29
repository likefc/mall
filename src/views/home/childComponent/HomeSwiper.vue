<template>
  <swiper>
    <swiper-item v-for="(item, index) in banners" :key="index">
      <a :href="item.link">
        <img :src="item.image" alt="" @load="imageLoad" />
      </a>
    </swiper-item>
  </swiper>
</template>
<script>
import { Swiper, SwiperItem } from 'components/common/swiper'
export default {
  name: 'homeSwiper',
  data() {
    return {
      isLoad: false
    }
  },
  props: {
    banners: {
      type: Array,
      default() {
        return []
      }
    }
  },
  components: {
    Swiper,
    SwiperItem
  },
  methods: {
    imageLoad() {
      if (!this.isLoad) {
        console.log('--- 轮播图图片加载 --')
        this.$emit('SwiperImgLoad')
        this.isLoad = true
      }
    }
  }
}
</script>
<style scoped></style>
