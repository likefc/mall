<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <scroll
      class="home-content"
      ref="scroll"
      :probe-type="3"
      @scrollPosition="scrollPosition"
      :pullUpLoad="true"
    >
      <home-swiper :banners="banners"></home-swiper>
      <home-recommend :recommends="recommends"></home-recommend>
      <home-feature></home-feature>

      <tab-control
        class="tab-control"
        :titles="['流行', '新款', '潮流']"
        @tabClcik="changeTab"
      ></tab-control>

      <goods-list :goods="tab"></goods-list>
    </scroll>
    <back-top class="home-back-top" @click.native="backTop" v-show="isShow" />
  </div>
</template>
<script>
import NavBar from "components/common/navbar/NavBar";
import Scroll from "components/common/scroll/Scroll";
import TabControl from "components/content/tabControl/TabControl";
import GoodsList from "components/content/goods/GoodsList";
import BackTop from "components/content/backTop/BackTop";

import HomeSwiper from "./childComponent/HomeSwiper";
import HomeRecommend from "./childComponent/HomeRecommend";
import HomeFeature from "./childComponent/HomeFeature";

import { getHomeMultidata, getHomeGoods } from "network/home";
import { log } from "util";
export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    HomeRecommend,
    HomeFeature,
    TabControl,
    GoodsList,
    Scroll,
    BackTop
  },
  computed: {
    tab() {
      return this.goods[this.currentType]["list"];
    }
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] }
      },
      currentType: "pop",
      isShow: false
    };
  },
  created() {
    //  请求多个数据
    this.getHomeMultidata();
    // 获取商品
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
    this.$bus.$on("goodsItemImg", () => {
      console.log("-------");
      this.$refs.scroll.refresh();
    });
  },
  methods: {
    changeTab(index) {
      console.log(index);
      switch (index) {
        case 0:
          this.currentType = "pop";
          break;
        case 1:
          this.currentType = "new";
          break;
        case 2:
          this.currentType = "sell";
          break;
        default:
          break;
      }
    },
    backTop() {
      this.$refs.scroll.scrollTo(0, 0, 500);
    },
    scrollPosition(position) {
      this.isShow = -position.y > 800;
    },
    // loadMore() {
    //   this.getHomeGoods(this.currentType);
    // },
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        const { banner, recommend } = res.data;
        this.banners = banner.list;
        this.recommends = recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then(data => {
        console.log(data);
        this.goods[type].list.push(...data.data.list);
        this.goods[page]++;
        this.$refs.scroll.finishPullUp();
      });
    }
  }
};
</script>
<style scoped>
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
.tab-control {
  position: sticky;
  top: 44px;
  background-color: #fff;
  z-index: 10;
}
.home-content {
  position: absolute;
  top: 44px;
  bottom: 49px;
  left: 0;
  right: 0;
}
</style>
