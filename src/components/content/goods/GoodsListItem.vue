<template>
  <!-- <div class='goods-list-item'>
    <img :src="goodsItem['show']['img']" alt="">
    <div class="goods-item-info">
      <p>{{goodsItem['title']}}</p>
      <span class='price'>{{goodsItem['price']}}</span>
      <span class='collect'>{{goodsItem['cfav']}}</span>
    </div>
  </div> -->
  <div class="goods-item">
    <img :src="goodsItem['show']['img']" @load="goodsItemImg" />
    <div class="goods-info">
      <p>{{ goodsItem.title }}</p>
      <span class="price">¥{{ goodsItem.price }}</span>
      <span class="collect">{{ goodsItem.cfav }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "GoodsListItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  components: {},
  methods: {
    goodsItemImg() {
      this.$bus.$emit("goodsItemImg");
    }
  }
};
</script>
<style>
.goods-item {
  padding-bottom: 40px;
  position: relative;
  /* width: 48%; */
  width: 48%;
}
.goods-item img {
  width: 100%;
  height: auto;
}

.goods-info {
  font-size: 12px;
  position: absolute;
  bottom: 5px;
  left: 0;
  right: 0;
  overflow: hidden;
  text-align: center;
}

.goods-info p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-bottom: 3px;
}

.goods-info .price {
  color: var(--color-high-text);
  margin-right: 20px;
}

.goods-info .collect {
  position: relative;
}

.goods-info .collect::before {
  content: "";
  position: absolute;
  left: -15px;
  top: 0;
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
}
</style>
