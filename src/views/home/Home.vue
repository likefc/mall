<template>
  <div id='home'>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'></home-swiper>
    <home-recommend :recommends='recommends'></home-recommend>
    <home-feature></home-feature>
  </div>
</template>
<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComponent/HomeSwiper'
import HomeRecommend from './childComponent/HomeRecommend'
import HomeFeature from './childComponent/HomeFeature'
import { getHomeMultidata } from 'network/home'
export default {
  name: 'Home',
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    //  请求多个数据
    getHomeMultidata().then(res => {
      const { banner, recommend } = res.data
      this.banners = banner.list
      this.recommends = recommend.list
    })
  },
  components: {
    NavBar,
    HomeSwiper,
    HomeRecommend,
    HomeFeature
  }
}
</script>
<style>
#home {
  padding-top: 44px;
  padding-bottom: 50px;
}
.home-nav {
  text-align: center;
  background-color: var(--color-tint);
  color: #fff;

  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  z-index: 100;
}
</style>
