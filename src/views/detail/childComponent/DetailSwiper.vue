<template>
  <div>
    <swiper class="swiper" v-if='!!topImages'>
      <swiper-item v-for="(item, index) in topImages" :key='index'>
        <!-- <img :src="item" alt=""> -->
        <a href="#">
          <img :src="item" alt="" />
        </a>
      </swiper-item>
    </swiper>
  </div>
</template>
<script>
import { Swiper, SwiperItem } from 'components/common/swiper'
export default {
  name: 'DetailSwiper',
  data() {
    return {}
  },
  props: {
    topImages: {
      type: Array,
      default() {
        return []
      }
    }
  },
  components: {
    Swiper,
    SwiperItem
  }
}
</script>
<style >
.swiper {
  height: 300px;
  overflow: hidden;
}
</style>
