<template>
    <div class='parallax-scroll'>
        <div class='angle-piece-occluder apo-top'>
          <div class='angle-piece ap-top' />
        </div>
        <div class='width-limiter' id='width-limiter'>
          <Portfolio v-on:view-details='viewDetails' 
                     v-bind:isCentered='!seeMoreInfo' 
                     v-bind:stateChange='stateChange'
                     v-bind:hexData='projects'
                      v-on:click.native='closeInfo'/>
          <PortfolioInfo v-bind:visible='seeMoreInfo' 
                         v-bind:stateChange='stateChange'
                         v-bind:hexData='projects'
                         v-bind:id='id'/>
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
import PortfolioInfo from '@/components/PortfolioInfo.vue';
import projects from '@/assets/projects.json';

let currY = 0;

export default {
  components: {
    Description,
    Portfolio,
    Contact,
    PortfolioInfo
  },
  data: function() {
    return {
      seeMoreInfo: false,
      stateChange: false,
      projects: projects,
      id: -1,
    };
  },
  methods: {
    closeInfo: function() {
      console.log("close");
      if (this.seeMoreInfo) {
        this.seeMoreInfo = false;
        setTimeout(() => document.body.classList.remove('no-scroll'), 1000);
      }
    },

    viewDetails: function(id) {
      this.id = id;
      this.openInfoWindow();
    },

    scrollHandlerUp: function() {this.scrollHandler(0)},
    scrollHandlerDown: function() {this.scrollHandler(1)},

    // Ensures vertical scrolling finishes before horizontal scrolling
    scrollHandler: function(upOrDown) {
      // TODO: Uhh theres probably a better way than repeating all of this...
      // Constants
      let scrollY = window.pageYOffset;

      let view_height = document.documentElement.clientHeight; // 943
      // let page_height = document.documentElement.scrollHeight; // 2998
      let hexagons_bcr = document
        .getElementById('width-limiter')
        .getBoundingClientRect(); // positions are relative to viewport
      let el_body = document.body;

      // Convert positions to absolute (relative to page instead of viewport)
      let viewport_top = scrollY;
      let viewport_bottom = scrollY + view_height;
      let hexagons_top = hexagons_bcr.top + scrollY;
      let hexagons_bottom = hexagons_bcr.bottom + scrollY;

      if (upOrDown === 0 && hexagons_top <= viewport_top) {
        window.removeEventListener('scroll', this.scrollHandlerUp);
        this.seeMoreInfo = true;
        this.stateChange = true;
        setTimeout(() => this.setUpWindowCloseHandler(), 200);
        setTimeout(() => el_body.classList.remove('no-scroll'), 1000);

      } else if (upOrDown === 1 && hexagons_bottom >= viewport_bottom) {
        window.removeEventListener('scroll', this.scrollHandlerDown);
        this.seeMoreInfo = true;
        this.stateChange = true;
        setTimeout(() => this.setUpWindowCloseHandler(), 200);
        setTimeout(() => el_body.classList.remove('no-scroll'), 1000);
      }
    },

    // Scrolls to the appropriate Y and opens the info window
    openInfoWindow: function() {
      // Constants
      let scrollY = window.pageYOffset;
      let view_height = document.documentElement.clientHeight; // 943
      let hexagons_bcr = document
        .getElementById('width-limiter')
        .getBoundingClientRect(); // positions are relative to viewport
      let el_body = document.body;

      // Convert positions to absolute (relative to page instead of viewport)
      let viewport_top = scrollY;
      let viewport_bottom = scrollY + view_height;
      let hexagons_top = hexagons_bcr.top + scrollY;
      let hexagons_bottom = hexagons_bcr.bottom + scrollY;

      el_body.classList.add('no-scroll');

      // Scroll down
      if (hexagons_top > viewport_top) {
        window.scrollTo({ top: hexagons_top + 10, behavior: 'smooth' });
        window.addEventListener('scroll', this.scrollHandlerUp)
      } else if (hexagons_bottom < viewport_bottom) {
      // Scroll up
        window.scrollTo({
          top: hexagons_bottom - view_height - 10,
          behavior: 'smooth'
        });
        window.addEventListener('scroll', this.scrollHandlerDown)
      } else {
        this.seeMoreInfo = true;
        this.stateChange = true;
        this.setUpWindowCloseHandler();
        setTimeout(() => el_body.classList.remove('no-scroll'), 1000);
      }
    },

    setUpWindowCloseHandler: function() {
      currY = window.pageYOffset;
      window.addEventListener('scroll', this.scrollLockToY);
    },

    scrollLockToY: function() {
      this.seeMoreInfo = false;
      window.scrollTo({top: currY});
      window.removeEventListener('scroll', this.scrollLockToY);
    }
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
  padding: 50px 0;
  padding-top: 0;
  padding-bottom: 0;
  box-sizing: border-box;
  display: block;
  margin: auto;
  position: relative;
}

.apo-top {
  position: absolute;
  top: -40vh;
}
.apo-bottom {
  top: 100%;
  position: absolute;
}

.angle-piece-occluder {
  width: 100%;
  height: 40vh;
  overflow: hidden;
  pointer-events: none;
}

.ap-top {
  transform: translate(-10vw, -10vh) rotateZ(-5deg);
}
.ap-bottom {
  transform: translate(-10vw, -60vh) rotateZ(-5deg);
}

.angle-piece {
  position: absolute;
  top: 100%;
  width: 120vw;
  height: 30vh;
  background-color: var(--parallax-bg-color);
  pointer-events: all;
  z-index: 1;
}
</style>

<style>
.no-scroll {
  height: 100%;
  overflow: hidden;
}
</style>

