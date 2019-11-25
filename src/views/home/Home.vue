<template>
  <div>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
  </div>
</template>
<script>
import NavBar from 'components/common/navbar/NavBar'
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
    NavBar
  }
}
</script>
<style>
.home-nav {
  text-align: center;
  background-color: var(--color-tint);
  color: #fff;
}
</style>
