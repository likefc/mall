<template>
  <div>
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
  </div>
</template>
<script>
import NavBar from "components/common/navbar/NavBar";
export default {
  name: "Home",
  data() {
    return {};
  },
  components: {
    NavBar
  }
};
</script>
<style>
nav-bar {
  text-align: center;
}
</style>
