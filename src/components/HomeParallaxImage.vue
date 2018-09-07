<template>
    <div class='parallax-image'>
      <div class='centered-text'> Hello There<span class='accent-text'>.</span></div>
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
  max-width: 100%;
  height: 100vh;
  background-image: url('../assets/tilable1.jpg');
  position: fixed;
  top: 0;
}

.accent-text {
  color: cyan;
  margin-left: -0.2em;
}

.centered-text {
  width: 100%;
  text-align: center;
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: calc(3em + 2vw);
  color: white;
  font-family: 'Montserrat', sans-serif;
  letter-spacing: 0.25em;
  word-spacing: 0.5em;
}
</style>