<template>
    <div class='parallax-scroll'>
        <div class='angle-piece-occluder apo-top'>
          <div class='angle-piece ap-top' />
        </div>
        <div class='width-limiter'>
          <Portfolio />
        </div>
        <div class='angle-piece-occluder apo-bottom'>
          <div class='angle-piece ap-bottom' />
        </div>
    </div>
</template>

<script>
import Description from '@/components/DescriptionCard.vue';
import Portfolio from '@/components/PortfolioCard.vue';
import Contact from '@/components/ContactCard.vue';

export default {
  name: 'HomeParallaxScroll',
  components: {
    Description,
    Portfolio,
    Contact,
  }
};
</script>

<style scoped>
.parallax-scroll {
  width: 100vw;
  max-width: 100%;
  background-color: red;
  background-color: var(--parallax-bg-color);
  margin-top: 105vh;
  position: relative;
  z-index: 1;
}

.width-limiter {
  background-color: var(--parallax-bg-color);
  width: 100%;
  max-width: 1200px;
  padding: 50px;
  padding-top: 0;
  padding-bottom: 0;
  box-sizing: border-box;
  display: block;
  margin: auto;
  position: relative;
}

.apo-top {
  position: absolute;
  top: -20vh;
}
.apo-bottom {
  top: 100%;
  position: absolute;
}

.angle-piece-occluder {
  width: 100%;
  height: 20vh;
  overflow: hidden;
  pointer-events: none;
}

.ap-top {
  transform: translate(-10vw, -10vh) rotateZ(-5deg);
}
.ap-bottom {
  transform: translate(-10vw, -30vh) rotateZ(-5deg);
}

.angle-piece {
  position: absolute;
  top: 100%;
  width: 120vw;
  height: 20vh;
  background-color: var(--parallax-bg-color);
  pointer-events: all;
  z-index: 1;
}
</style>
