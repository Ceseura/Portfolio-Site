<template>
  <div class="home">
    <HomeParallaxImage />
    <HomeParallaxScroll/>
    <!-- </HomeParallaxScroll> -->
  </div>
</template>

<script>
// @ is an alias to /src
import HomeParallaxImage from '@/components/HomeParallaxImage.vue';
import HomeParallaxScroll from '@/components/HomeParallaxScroll.vue';

export default {
  name: 'home',
  components: {
    HomeParallaxImage,
    HomeParallaxScroll
  }
};
</script>

<style>
.home {
  --parallax-text-color: black;
}
</style>