<template>
    <div class='parallax-scroll'>
        <div class='angle-piece-occluder'>
            <div class='angle-piece' />
        </div>
        <div class='width-limiter'>
            <Portfolio />
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
  height: auto;
  background-color: var(--parallax-bg-color);
  position: absolute;
  top: 105vh;
}

.angle-piece-occluder {
  width: 100%;
  height: 20vh;
  overflow: hidden;
  position: relative;
  top: -20vh;
  pointer-events: none;
}

.angle-piece {
  position: absolute;
  top: 100%;
  width: 120vw;
  height: 20vh;
  background-color: var(--parallax-bg-color);
  transform: translate(-10vw, -10vh) rotateZ(-5deg);
  pointer-events: all;
  z-index: 1;
}

.width-limiter {
  background-color: var(--parallax-bg-color);
  width: 100%;
  max-width: 1200px;
  padding: 50px;
  padding-top: 0;
  box-sizing: border-box;
  display: block;
  margin: auto;
  position: relative;
  top: -10vh;
}
</style>
