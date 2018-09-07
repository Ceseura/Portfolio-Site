<template>
    <div class='portfolio-card'>
        <div class='title'> My Projects </div>
        <div class='hexagons'>
            <ul class='hex-grid clear'>
                <li is='Hexagon' 
                  v-for='i in numberHexagons' 
                  v-bind:key='i' 
                  v-bind:state='hexLayout[i-1]' 
                  v-bind:hexData='getHexData(hexLayout[i-1])'>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Hexagon from '@/components/PortfolioCardHexagon.vue';
import data from '@/assets/projects.json';

var a = [1, -1, 6, 0,
         -1, 2, 4, 0,
         -1, 3, -1 ,0,
         0, 5, 0];

export default {
  components: {
    Hexagon,
  },
  data: function() {
    return {
      numberHexagons: 15,
      hexLayout: a,
    };
  },
  methods: {
    getHexData: function(i) {
      if (i > 0) {
        return data.projects[i-1];
      } else {
        return null;
      }
    }
  }
};
</script>

<style scoped>
.title {
  padding-left: 40px;
  color: var(--text-color);
  font-size: 60px;
  font-family: 'Montserrat', sans-serif;
  width: 100%;
  border-bottom: 1px solid var(--text-color);
}

.hex-grid {
  position: relative;
  padding: 0;
  margin-left: 5%;
  margin-bottom: 20%;
}

.clear:after {
  content: '';
  display: block;
  clear: both;
}
</style>
