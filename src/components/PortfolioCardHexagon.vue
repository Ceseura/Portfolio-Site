<template>
    <div class='hexagon-outer'>
        <div class='hexagon-inner' 
            v-bind:style='finalStyles' 
            v-on:mouseenter='mouseEnter'
            v-on:mouseleave='mouseLeave'
            v-if='this.state != -1'>

          <div class='hexagon-title'> {{ this.title }} </div>
          <div class='hexagon-tag-container' v-if='this.isActive'>
            <div class='hexagon-tag' 
              v-for='tag in this.tags'
              v-bind:key='tag'> {{tag}} </div>
          </div>    

        </div>
    </div>
</template>

<script>
var colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];

export default {
  props: {
    state: Number,
    title: String,
    tags: Array,
  },
  data: function() {
    return {
      colorStyle: {
        backgroundColor: colors[Math.floor(Math.random() * colors.length)]
      },
      activeStyle: {
        backgroundImage: 'radial-gradient(transparent 40%, grey)',
        cursor: 'pointer',
      },
      isActive: false,
    }
  },

  computed: {
    finalStyles: function() {
      var outStyles = Object.assign({}, this.colorStyle, this.isActive ? this.activeStyle : null);
      return outStyles;
    }
  },

  methods: {
    mouseEnter: function() {
      if (this.state > 0) 
        this.isActive = true;
    },
    mouseLeave: function() {
      this.isActive = false;
    }
  }
};
</script>

<style scoped>
/* Oh god what even is going on here rotations and skew are confuse */
.hexagon-title {
  width: 100%;
  height: 48%; /* 48 is a magic number */
  margin: 30% 15%;
  transform: rotate(-90deg);
  text-align: center;
  font-size: calc(1em + 1vw);
}

/* make me responsive pls  */
@media (min-width: 800px) {
.hexagon-tag-container {
  position: absolute;
  width: 65%;
  height: 40%;
  top: 30%;
  right: -20px;
  transform: rotate(-90deg);
  overflow: hidden;
  text-align: center;
  animation-name: tags-enterFromBottom;
  animation-duration: 0.5s;
}
}

@keyframes tags-enterFromBottom {
  0% {right: calc(-40% - 20px)}
  100% {right: -20px}
}

.hexagon-tag {
  display: inline-block;
  background-color: white;
  padding: 3px;
  margin: 2.5px;
  font-size: 12px;
}

.hexagon-outer:nth-child(2n) {
  margin-left: -2%;
  margin-right: -2%;
  transform: translateY(46%) rotate(30deg) skewY(30deg);
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
  overflow: hidden;
}
</style>
