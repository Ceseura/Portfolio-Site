<template>
    <div class='portfolio-card' v-bind:class='[stateChange ? isCentered ? "centered" : "lefted" : null]'>
        <div class='title'> My Projects </div>
        <div class='hexagons'>
            <ul class='hex-grid clear'>
                <li is='Hexagon' 
                  v-on:view-details='viewDetails'
                  v-for='i in hexLayout.length' 
                  v-bind:key='i' 
                  v-bind:state='hexLayout[i - 1]' 
                  v-bind:hexData='getHexData(hexLayout[i - 1])'>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Hexagon from '@/components/PortfolioCardHexagon.vue';

var a = [1, 0, 6, 0, 0, 2, 4, 0, 3, , 0, 7, 0, 5, 0, 0, 0, 0, 0, 0];

export default {
  components: {
    Hexagon
  },
  data: function() {
    return {
      hexLayout: a
    };
  },
  props: {
    isCentered: Boolean,
    stateChange: Boolean,
    hexData: Object
  },
  methods: {
    getHexData: function(i) {
      if (i > 0) {
        return this.hexData.projects[i - 1];
      } else {
        return null;
      }
    },
    viewDetails: function(id, event) {
      event.stopPropagation();
      this.$emit('view-details', id);
    }
  }
};
</script>

<style scoped>
.portfolio-card {
  width: 60vw;
  padding-top: 50px;
  margin-left: 20%;
  min-height: 100vh;
}

.lefted {
  margin-left: 0%;
  animation-name: hexagons_moveToLeft;
  animation-duration: 1s;
  animation-timing-function: ease;
}

.centered {
  margin-left: 20%;
  animation-name: hexagons_moveToCenter;
  animation-duration: 1s;
  animation-timing-function: ease;
}

@keyframes hexagons_moveToLeft {
  0% {
    margin-left: 20%;
  }
  100% {
    margin-left: 0%;
  }
}

@keyframes hexagons_moveToCenter {
  0% {
    margin-left: 0%;
  }
  100% {
    margin-left: 20%;
  }
}

.title {
  padding-left: 40px;
  box-sizing: border-box;
  color: var(--text-color);
  font-size: 60px;
  font-family: 'Montserrat', sans-serif;
  border-bottom: 1px solid var(--text-color);
}

.hex-grid {
  position: relative;
  padding: 0;
  margin-left: 5%;
  padding-bottom: 20%;
}

.clear:after {
  content: '';
  display: block;
  clear: both;
}
</style>
