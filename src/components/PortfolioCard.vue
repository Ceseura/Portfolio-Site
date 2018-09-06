<template>
    <div class='portfolio-card'>
        <div class='title'> Placeholder Text </div>
        <div class='hexagons'>
            <ul class='hex-grid clear'>
                <li v-for='i in numberHexagons' v-bind:key='i' class='hexagon-outer'>
                    <div class='hexagon-inner' v-bind:class='randomColor()'> Test </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: 'PortfolioCard',
  data: function() {
    return {
      numberHexagons: 16
    };
  },
  methods: {
    randomColor: function() {
      var colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];
      return colors[Math.floor(Math.random() * colors.length)];
    }
  }
};
</script>

<style scoped>
.title {
  color: var(--text-color);
  font-size: 40px;
  width: 100%;
  border-bottom: 1px solid var(--text-color);
}

.hex-grid {
  position: relative;
  padding: 0;
  margin-left: 5%;
  margin-bottom: 20%;
}

.hexagon-outer:nth-child(2n) {
  margin-left: -2%;
  margin-right: -2%;
  transform: translateY(46%) rotate(30deg) skewY(30deg);
}

.clear:after {
  content: '';
  display: block;
  clear: both;
}

.hexagon-outer {
  list-style-type: none;
  position: relative;
  float: left;
  width: 25.0714285714%;
  padding: 0 0 28.9508413065% 0;
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
}

.red {
  background-color: red;
}
.orange {
  background-color: orange;
}
.yellow {
  background-color: yellow;
}
.green {
  background-color: green;
}
.blue {
  background-color: blue;
}
.purple {
  background-color: purple;
}
</style>
