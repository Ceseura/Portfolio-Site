<template>
    <div class='hexagon-outer responsive-hexagon'>
        <div class='hexagon-inner' 
            v-on:mouseenter='mouseEnter'
            v-on:mouseleave='mouseLeave'
            v-if='this.state != -1'>
          <div class='bg-image' v-bind:style='finalStyles' v-on:click='state > 0 ? $emit("view-details", hexData.id, $event) : null'/>
          <a class='hexagon-content' v-if='this.isActive'>
            <div class='hexagon-title'> {{ this.hexData.name }} </div>
          </a>

        </div>
    </div>
</template>

<script>
var inactiveColors = [
  '#ffafaf',
  '#ffa3a3',
  '#ff8e8e',
  '#ffb78e',
  '#ffdab2',
  '#deffd3',
  '#f1ff8e',
  '#e1ffb2',
  '#d3ffe7',
  '#c6ff8e',
  '#c0ffb2',
  '#d3fff9',
  '#8effaa',
  '#b2ffd1',
  '#d3f2ff',
  '#8effe1',
  '#b2fff6',
  '#d3e2ff',
  '#8ee6ff',
  '#b2d3ff',
  '#d3d3ff',
  '#8eaaff',
  '#c6b2ff',
  '#e1d3ff',
  '#a58eff',
  '#ebb2ff',
  '#f4d3ff'
];

export default {
  props: {
    state: Number,
    hexData: Object
  },
  data: function() {
    return {
      colorStyle: {
        backgroundColor:
          inactiveColors[Math.floor(Math.random() * inactiveColors.length)]
      },
      pictureStyle: {
        backgroundImage:
          this.state > 0
            ? 'url(' +
              require('../assets/hexagon-icons/' + this.hexData.icon_url) +
              ')'
            : null,
        backgroundSize: 'contain'
      },
      activeStyle: {
        backgroundImage:
          this.state > 0
            ? 'linear-gradient(rgba(240, 240, 240, 0.8), rgba(240, 240, 240, 0.8)), url(' +
              require('../assets/hexagon-icons/' + this.hexData.icon_url) +
              ')'
            : null,
        cursor: 'pointer'
      },
      isActive: false
    };
  },

  computed: {
    finalStyles: function() {
      var outStyles = Object.assign(
        {},
        this.state > 0 ? this.pictureStyle : this.colorStyle,
        this.isActive ? this.activeStyle : null
      );
      return outStyles;
    }
  },

  methods: {
    mouseEnter: function() {
      if (this.state > 0) this.isActive = true;
    },
    mouseLeave: function() {
      this.isActive = false;
    }
  }
};
</script>

<style scoped>
.bg-image {
  width: 115%;
  padding-top: 115%;
  position: absolute;
  transform: rotate(-90deg) translate(0, -7%);
}
/* Oh god what even is going on here rotations and skew are confuse */
.hexagon-content {
  position: absolute;
  transform: rotate(-90deg) translate(-9%, 0%);
  width: 100%;
  height: 85%;
  animation-name: content-enterFromBottom;
  animation-duration: 0.3s;
  pointer-events: none;
}

.hexagon-content:hover {
  cursor: pointer;
}

.hexagon-title {
  width: 90%;
  padding-left: 5%;
  padding-top: 25%;
  position: absolute;
  bottom: 50%;
  text-align: center;
  font-size: calc(1em + 0.5vw);
  font-family: 'Montserrat', sans-serif;
  font-weight: bold;
}

.hexagon-tag-container {
  position: absolute;
  top: 55%;
  left: 50%;
  transform: translateX(-50%);
  min-height: 30%;
  width: 60%;
  overflow: hidden;
  text-align: center;
}

@keyframes content-enterFromBottom {
  0% {
    right: calc(-100% - 115%);
  }
  100% {
    right: -15%;
  }
}

.hexagon-tag {
  display: inline-block;
  background-image: linear-gradient(to bottom, #ffffff, #e5e5e5);
  padding: 3px 7px;
  margin: 2px 4px;
  font-size: 16px;
  border-radius: 2px;
  border-bottom: 2px solid black;
}

.responsive-hexagon {
  /* width: 220px;
  padding-top: 254px; */
  /* width: 200px;
  padding-top: 231px; */
  width: 180px;
  padding-top: 208px;
}

/* width * factor: 1.15473441109 */

/* 2 columns */
@media (min-width: 625px) and (max-width: 909px) {
  /* .responsive-hexagon {
    width: 45.1285714285%;
    padding: 0 0 52.1115143517% 0;
  } */
  .hexagon-outer:nth-child(2n) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
}

/* 3 columns */
@media (min-width: 910px) and (max-width: 1214px) {
  /* .responsive-hexagon {
    width: 32.5928571428%;
    padding: 0 0 37.6360936984% 0;
  } */
  .hexagon-outer:nth-child(3n + 2) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
}

/* 4 columns */
@media (min-width: 1215px) and (max-width: 1464px) {
  /* .responsive-hexagon {
    width: 24.8207142857%;
    padding: 0 0 28.6613328934% 0;
  } */
  .hexagon-outer:nth-child(2n) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
}

/* 5 columns */
@media (min-width: 1465px) and (max-width: 1754) {
  /* .responsive-hexagon {
    width: 19.8565714286%;
    padding: 0 0 22.9290663147% 0;
  } */
  .hexagon-outer:nth-child(5n + 2) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
  .hexagon-outer:nth-child(5n + 4) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
}

/* 6 columns */
@media (min-width: 1755px) {
  /* .responsive-hexagon {
    width: 19.8565714286%;
    padding: 0 0 22.9290663147% 0;
  } */
  .hexagon-outer:nth-child(2n) {
    margin-left: -2%;
    margin-right: -2%;
    transform: translateY(46%) rotate(30deg) skewY(30deg);
  }
}

.hexagon-outer {
  list-style-type: none;
  position: relative;
  float: left;
  transform: rotate(30deg) skewY(30deg);
  overflow: hidden;
  visibility: hidden;
  margin-bottom: -2%;
}

.hexagon-inner {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transform: skewY(-30deg) rotate(60deg);
  visibility: visible;
  overflow: hidden;
}
</style>
