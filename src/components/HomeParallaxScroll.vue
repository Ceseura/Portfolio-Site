<template>
    <div class='parallax-scroll'>
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
    PortfolioCard,
  }
};
</script>

<style scoped>
.parallax-scroll {
  width: 100vw;
  height: 100%;
  background-color: var(--description-bg-color);
  position: absolute;
  top: 105vh;
}
.parallax-scroll:before {
    content: "";
    display: inline-block;
    width: 120vw;
    height: 30vh;
    transform: translate(-10vw, -10vh) rotateZ(-5deg);
    background-color: var(--description-bg-color);
}

.width-limiter {
    height: 1000px;
    background-color: blue;
    width: 100%;
    max-width: 800px;
    position: absolute;
    left: 50%;
    top: 0;
    transform: translate(-50%, 0);
    padding: 40px;   
    /* display: block;
    margin: auto;
    padding: 40px; */
}
</style>