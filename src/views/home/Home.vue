<!--  -->
<template>
  <div class="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
  </div>
</template>

<script>
import  NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/HomeRecommendView'
import FeatureView from './childComps/FeatureView'

import {getHomeMultidata} from 'network/home'

export default {
  data () {
    return {
      banners: [],
      recommends: []
    };
  },
  created() {
    getHomeMultidata().then(res => {
      console.log(res)
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list
    })
  },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView
  }
}

</script>
<style>
.home {
  padding-top: 44px;
}

.home-nav {
  background-color: var(--color-tint);
  color: #ffffff;
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  z-index: 9;
} 
</style>