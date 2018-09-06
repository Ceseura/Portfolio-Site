<template>
    <div class='parallax-image'>
      <div class='centered-text'> Placeholder Text </div>
    </div>
</template>

<script>
export default {
  name: 'HomeParallaxImage'
};
</script>

<style scoped>
.parallax-image {
  width: 100vw;
  height: 100vh;
  background: linear-gradient(red, green);
  position: fixed;
  top: 0;
}

.centered-text {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 80px;
  color: var(--parallax-text-color);
}
</style>