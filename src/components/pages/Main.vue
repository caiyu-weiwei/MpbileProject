<template>
  <div>
    <div class="main-div">
      <!-- 路由匹配到的组件将渲染在这里 -->
      <keep-alive>
        <router-view/>
      </keep-alive>
    </div>
    <van-tabbar v-model="active" @change="handleChangeTabbar(active)">
      <van-tabbar-item icon="shop">首页</van-tabbar-item>
      <van-tabbar-item icon="records">列表</van-tabbar-item>
      <van-tabbar-item icon="cart">购物车</van-tabbar-item>
      <van-tabbar-item icon="contact">会员中心</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>
export default {
  data () {
    return {
      active: 0
    }
  },
  created () {
    this.getActiveIcon()
  },
  // Main.vue是父页面，它里面有好多子页面，子页面变化不能保证icon的索引变更,起到底部导航与页面时时变化
  updated () {
    this.getActiveIcon()
  },
  methods: {
    // 底部导航路由跳转
    handleChangeTabbar (active) {
      console.log(active)
      switch (active) {
        case 0:
          this.$router.push({name: 'ShoppingMall'})
          break
        case 1:
          this.$router.push({name: 'CategoryList'})
          break
        case 2:
          this.$router.push({name: 'Cart'})
          break
        case 3:
          this.$router.push({name: 'Member'})
          break
      }
    },
    // 底部导航icon高亮
    getActiveIcon () {
      let activePath = this.$route.path
      if (activePath === '/Cart') this.active = 2
    }
  }
}
</script>

<style scoped>
</style>
