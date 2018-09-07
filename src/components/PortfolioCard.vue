<template>
    <div class='portfolio-card'>
        <div class='title'> Placeholder Text </div>
        <div class='hexagons'>
            <ul class='hex-grid clear'>
                <li is='Hexagon' 
                  v-for='i in numberHexagons' 
                  v-bind:key='i' 
                  v-bind:state='hexLayout[i-1]' 
                  v-bind:title='hexTitles[hexLayout[i-1]]'
                  v-bind:tags='hexTags[hexLayout[i-1]]'>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Hexagon from '@/components/PortfolioCardHexagon.vue';

var a = [1, 0, 0, 0,
         0, 2, 4, 0,
         0, -1, 3 ,0,
         0, 0, 0, 0];

// extract to json?
var b = ['', 'Placeholder 1', 'title 2', 'project 3', 'listitem 4'];
var c = [[], ['Python', 'AWS'], ['Angular2', 'mySQL', 'Bootstrap'], ['React', 'Redux', 'Jenkins', 'Hibernate'], ['Vue.js']];

export default {
  name: 'PortfolioCard',
  components: {
    Hexagon,
  },
  data: function() {
    return {
      numberHexagons: 16,
      hexLayout: a,
      hexTitles: b,
      hexTags: c,
    };
  }
};
</script>

<style scoped>
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
