<template>
    <div class='parallax-scroll'>
        <div class='angle-piece-occluder'>
            <div class='angle-piece' />
        </div>
        <div class='width-limiter'>
            <DescriptionCard />
            <PortfolioCard />
        </div>
    </div>
</template>

<script>
import DescriptionCard from '@/components/DescriptionCard.vue';
import PortfolioCard from '@/components/PortfolioCard.vue';

export default {
  name: 'HomeParallaxScroll',
  components: {
    DescriptionCard,
    PortfolioCard
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
}

.angle-piece {
  position: absolute;
  top: 100%;
  width: 120vw;
  height: 30vh;
  background-color: var(--parallax-bg-color);
  transform: translate(-10vw, -10vh) rotateZ(-5deg);
}

.width-limiter {
  background-color: var(--description-bg-color);
  width: 100%;
  max-width: 1000px;
  padding: 50px;
  display: block;
  margin: auto;
  position: relative;
  top: -10vh;
}
</style>
