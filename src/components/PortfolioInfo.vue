<template>
    <div class='portfolio-info' 
         v-bind:class='[stateChange ? 
                        visible ? "dramatic-entrance" : "dramatic-exit" : 
                        null]'> 
        Placeholder 
    </div>
</template>

<script>
export default {
  props: {
    visible: Boolean,
    stateChange: Boolean,
    hexData: Object,
  },
  watch: {
    visible: function() {
      console.log(this.visible)
    }
  }
}
</script>

<style scoped>
.portfolio-info {
  background-color: red;
  height: 100vh;
  width: 40%;
  position: fixed;
  top: 0;
  right: -40%;
}

.dramatic-entrance {
  animation-name: info_enterFromRight;
  animation-duration: 1s;
  animation-timing-function: ease;
  right: 0;
}

.dramatic-exit {
  animation-name: info_exitToRight;
  animation-duration: 1s;
  animation-timing-function: ease;
  right: -40%;
}

@keyframes info_enterFromRight {
  0% {
    right: -40%;
  }
  100% {
    right: 0;
  }
}

@keyframes info_exitToRight {
  0% {
    right: 0;
  }
  100% {
    right: -40%;
  }
}
</style>
