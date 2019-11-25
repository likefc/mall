<template>
  <div>
    <nav-bar class="home-nav">
      <div slot="center" class='navbarCenter'>
        购物街
      </div>
    </nav-bar>
  </div>
</template>
<script>
import NavBar from 'components/common/navbar/NavBar'
export default {
  name: 'Home',
  data() {
    return {}
  },
  components: {
    NavBar
  }
}
</script>
<style scoped>
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
.navbarCenter {
  text-align: center;
}
</style>
