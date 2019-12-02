<template>
  <div>
    <detail-nav-bar></detail-nav-bar>
    <detail-swiper :topImages='topImages'></detail-swiper>
  </div>
</template>
<script>
import DetailNavBar from './childComponent/DetailNavBar'
import DetailSwiper from './childComponent/DetailSwiper'

import { getDetail } from 'network/detail'

export default {
  name: 'Detail',

  data() {
    return {
      iid: null,
      topImages: []
    }
  },
  created() {
    //  保存iid
    this.iid = this.$route.params.id
    //  请求数据
    getDetail(this.iid).then(res => {
      console.log(res)
      this.topImages = res.result.itemInfo.topImages
    })
  },

  components: {
    DetailNavBar,
    DetailSwiper
  }
}
</script>
<style>
</style>
