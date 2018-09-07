<template>
    <div class='parallax-image'>
      <a href='https://github.com/Karavis'>
        <div class='github link-circle' v-on:mouseenter='show_tooltip(1)' v-on:mouseleave='hide_tooltip(1)'/>
        <div class='occluder height-offset1'>
          <div class='github-tooltip link-tooltip' v-if='this.show_github'> Github </div>
        </div>
      </a>
      <a href='https://www.linkedin.com/in/alexander-liang-7070b9167/'>
        <div class='linkedin link-circle' v-on:mouseenter='show_tooltip(2)' v-on:mouseleave='hide_tooltip(2)'/>
        <div class='height-offset2 occluder'>
          <div class='linkedin-tooltip link-tooltip' v-if='this.show_linkedin'> Linkedin </div>
        </div>
      </a>

      <div class='centered-text'> Hello There<span class='accent-text'>.</span></div>
      <div class='down-arrow' v-on:click='scrollDown()'>
        <svg width='70px' height='70px'>
          <path class='paintbrush-settings arrow' d='m40 20 L55 35 L40 50 M55 35 H20 35' />
          <circle class='paintbrush-settings outline-circle' cx='35' cy='35' r='30px' />
        </svg>
      </div>
    </div>
</template>

<script>
// arrow animation
// https://codepen.io/AlexandreJolly/pen/oWQMoG

export default {
  data: function() {
    return {
      show_github: false,
      show_linkedin: false,
    }
  },
  methods: {
    scrollDown: function () {
      var scrollTarget = document.querySelector('.width-limiter');
      scrollTarget.scrollIntoView({behavior: 'smooth', block: 'start'});
    },
    show_tooltip: function(i) {
      if (i === 1) {
        this.show_github = true;
      } else if (i === 2) {
        this.show_linkedin = true;
      }
    },
    hide_tooltip: function(i) {
      if (i === 1) {
        this.show_github = false;
      } else if (i === 2) {
        this.show_linkedin = false;
      }
    }
  }
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

.occluder {
  position: absolute;
  right: 80px;
  height: 50px;
  width: 100px;
  overflow: hidden;
}

.height-offset1 {
  top: 20px;
}

.height-offset2 {
  top: 90px;
}

.github {
  background-image: url('../assets/github.png');
  background-size: 50px 50px;
  top: 0;
  right: 0;
}

.linkedin {
  background-image: url('../assets/linkedin.png');
  background-size: 50px 50px;
  top: 70px;
  right: 0;
}

.link-circle {
  height: 50px;
  width: 50px;
  position: absolute;
  margin: 20px;
}

.link-circle:hover {
  cursor: pointer;
}

.link-tooltip {
  color: white;
  font-size: 1em;
  font-family: 'Montserrat', sans-serif;
  position: absolute;
  animation-name: tooltip_enterFromRight;
  animation-duration: 1s;
  top: 15px;
  right: 0px;
}

@keyframes tooltip_enterFromRight {
  0% {right: -100px;}
  100% {right: 0px;}
}

.accent-text {
  color: cyan;
  margin-left: -0.1em;
  font-size: calc(1em + 3vw);
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

.down-arrow {
  position: absolute;
  top: 85vh;
  left: 50%;
  transform: translate(-50%,  0) rotate(90deg);
}

.paintbrush-settings {
  stroke: white;
  stroke-width: 2;
  stroke-linejoin: round;
  stroke-miterlimit: 10; 
  fill: none;
}

.outline-circle {
  stroke-dasharray: 300;
  stroke-dashoffset: 300;
  fill: transparent;
}

.outline-circle:hover {
  animation-name: animate-circle;
  animation-duration: 1s;
  animation-timing-function: ease;
  stroke-dashoffset: 0;
  cursor: pointer;
}

@keyframes animate-circle {
  0% {stroke-dashoffset: 300}
  100% {stroke-dashoffset: 0}
}
</style>