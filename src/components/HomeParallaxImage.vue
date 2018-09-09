<template>
    <div class='parallax-image'>
      <div class='mobile-warning mw-responsive'> Warning: this site is not designed for small screens! Please come back on a larger device for the intended experience. </div>
      <a href='https://github.com/Karavis'>
        <div class='github link-circle' v-on:mouseenter='show_tooltip(1)' v-on:mouseleave='hide_tooltip(1)'/>
        <div class='occluder height-offset1'>
          <div class='link-tooltip' v-if='this.show_github'> Github </div>
        </div>
      </a>
      <a href='mailto:myboringemail4@gmail.com'>
        <div class='email link-circle' v-on:mouseenter='show_tooltip(4)' v-on:mouseleave='hide_tooltip(4)'/>
        <div class='height-offset2 occluder'>
          <div class='link-tooltip' v-if='this.show_email'> Email </div>
        </div>
      </a>
      <a href='https://www.linkedin.com/in/alexander-liang-7070b9167/'>
        <div class='linkedin link-circle' v-on:mouseenter='show_tooltip(2)' v-on:mouseleave='hide_tooltip(2)'/>
        <div class='height-offset3 occluder'>
          <div class='link-tooltip' v-if='this.show_linkedin'> Linkedin </div>
        </div>
      </a>
      <a href='https://drive.google.com/file/d/0Bzt4QEceUnY6NFhXRTIwSy1JMXM/view'>
        <div class='resume link-circle' v-on:mouseenter='show_tooltip(3)' v-on:mouseleave='hide_tooltip(3)'/>
        <div class='height-offset4 occluder'>
          <div class='link-tooltip' v-if='this.show_resume'> Resume </div>
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
      show_resume: false,
      show_email: false
    };
  },
  methods: {
    scrollDown: function() {
      var scrollTarget = document.querySelector('.width-limiter');
      scrollTarget.scrollIntoView({ behavior: 'smooth', block: 'start' });
    },
    show_tooltip: function(i) {
      if (i === 1) {
        this.show_github = true;
      } else if (i === 2) {
        this.show_linkedin = true;
      } else if (i === 3) {
        this.show_resume = true;
      } else if (i === 4) {
        this.show_email = true;
      }
    },
    hide_tooltip: function(i) {
      if (i === 1) {
        this.show_github = false;
      } else if (i === 2) {
        this.show_linkedin = false;
      } else if (i === 3) {
        this.show_resume = false;
      } else if (i === 4) {
        this.show_email = false;
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

@media (max-width: 665px) {
  .mw-responsive {
    visibility: show;;
  }
}

@media (min-width: 666px) {
  .mw-responsive {
    visibility: hidden;
  }
}

.mobile-warning {
  position: absolute;
  left: 50%;
  top: 15%;
  transform: translate(-50%, -50%);
  padding: 10px 10px;
  color: black;
  text-align: center;
  font-family: 'Montserrat', sans-serif;
  font-size: calc(1em + 0.3vw);
  background-color: rgb(255, 127, 127);
  border-radius: 10px;
}

.occluder {
  position: absolute;
  right: 70px;
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

.height-offset3 {
  top: 160px;
}

.height-offset4 {
  top: 230px;
}

.email {
  background-image: url('../assets/button-presets/email_dark.png');
  background-size: 50px 50px;
  top: 70px;
  right: 0;
}
.email:hover {
  background-image: url('../assets/button-presets/email_light.png');
}

.github {
  background-image: url('../assets/button-presets/github_dark.png');
  background-size: 50px 50px;
  top: 0;
  right: 0;
}
.github:hover {
  background-image: url('../assets/button-presets/github_light.png');
}

.linkedin {
  background-image: url('../assets/button-presets/linkedin_dark.png');
  background-size: 50px 50px;
  top: 140px;
  right: 0;
}
.linkedin:hover {
  background-image: url('../assets/button-presets/linkedin_light.png');
}

.resume {
  background-image: url('../assets/button-presets/resume_dark.png');
  background-size: 50px 50px;
  top: 210px;
  right: 0;
}
.resume:hover {
  background-image: url('../assets/button-presets/resume_light.png');
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
  right: 10px;
}

@keyframes tooltip_enterFromRight {
  0% {
    right: -100px;
  }
  100% {
    right: 10px;
  }
}

.accent-text {
  color: cyan;
  margin-left: -0.1em;
  font-size: calc(1em + 3vw);
}

.centered-text {
  padding: 0 10%;
  width: 80%;
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
  transform: translate(-50%, 0) rotate(90deg);
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
  0% {
    stroke-dashoffset: 300;
  }
  100% {
    stroke-dashoffset: 0;
  }
}
</style>
