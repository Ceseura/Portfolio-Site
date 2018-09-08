<template>
  <div class="home">
    <HomeParallaxImage />
    <HomeParallaxScroll />
    <ContactParallaxBg />
    <div class='spacer-105vh' />
  </div>
</template>

<script>
// @ is an alias to /src
import HomeParallaxImage from '@/components/HomeParallaxImage.vue';
import HomeParallaxScroll from '@/components/HomeParallaxScroll.vue';
import ContactParallaxBg from '@/components/ContactCard.vue';

export default {
  name: 'home',
  components: {
    HomeParallaxImage,
    HomeParallaxScroll,
    ContactParallaxBg
  }
};
</script>

<style>
.home {
  height: 100%;
}

.spacer-105vh {
  height: 105vh;
  width: 100%;
}
</style>
