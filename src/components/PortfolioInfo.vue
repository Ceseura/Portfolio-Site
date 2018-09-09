<template>
    <div class='portfolio-info' 
         v-bind:class='[stateChange ? 
                        visible ? "dramatic-entrance" : "dramatic-exit" : 
                        null]'> 
      <div class='item-info-box'>
        <div class='button-box'>
          <a v-bind:href='myHexData.github_url'>
            <div class='item-github-link'/>
          </a>
          <a v-bind:href='myHexData.link_url'>
            <div class='item-link' v-bind:class='[myHexData.link_url ? null : "item-link-inactive"]'/>
          </a>
        </div>
        <div class='item-info-title'>{{this.myHexData.name}}</div>
        <div class='item-info-dash'/>
        <div class='item-info-description' v-html='myHexData.description'/>
        <div class='item-info-dash'/>
        <div class='item-info-tags'>
          <div class='item-info-tag' v-for='tag in myHexData.tags' v-bind:key='tag'> {{tag}} </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  props: {
    visible: Boolean,
    stateChange: Boolean,
    hexData: Object,
    id: Number
  },
  data: function() {
    return {
      myHexData: this.hexData.projects[0]
    };
  },
  methods: {
    getHexData: function(id) {
      if (id == -1) return null;
      else {
        return this.hexData.projects[id];
      }
    }
  },
  watch: {
    id: function() {
      this.myHexData = this.getHexData(this.id);
    }
  }
};
</script>

<style scoped>
.portfolio-info {
  background-color: rgb(0, 190, 190);
  height: 100vh;
  width: 40vw;
  position: fixed;
  top: 0;
  left: 100vw;
  z-index: 5;
}

.button-box {
  position: absolute;
  top: 0;
  left: -10%;
  width: 5%;
}

.item-github-link {
  background-image: url('../assets/button-presets/source_light.png');
  background-size: cover;
  width: 100%;
  padding-top: 100%;
  margin-bottom: 40%;
}

.item-github-link:hover {
  cursor: pointer;
  background-image: url('../assets/button-presets/source_dark.png');
}

.item-link {
  background-image: url('../assets/button-presets/link_light.png');
  background-size: cover;
  width: 100%;
  padding-top: 100%;
}

.item-link:hover {
  cursor: pointer;
  background-image: url('../assets/button-presets/link_dark.png');
}

.item-link-inactive {
  background-image: url('../assets/button-presets/link_grey.png');
  cursor: not-allowed;
}

.item-link-inactive:hover {
  background-image: url('../assets/button-presets/link_grey.png');
  cursor: not-allowed;
}

.item-info-box {
  width: 70%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.item-info-tags {
  width: 100%;
  height: 100px;
  margin-top: 3em;
}

.item-info-tag {
  color: white;
  font-family: 'Montserrat', sans-serif;
  font-size: calc(0.3em + 0.8vw);
  border: 1px solid white;
  display: inline-block;
  padding: 5px 20px;
  border-radius: 100px;
  margin: 5px 5px;
  cursor: default;
}

.item-info-dash {
  width: 5%;
  border-bottom: 5px solid darkcyan;
}

.item-info-description {
  color: white;
  font-size: calc(1em + 0.3vw);
  font-family: 'Source Sans Pro', sans-serif;
  line-height: 1.5em;
  font-weight: 200;
  margin-top: 2em;
  margin-bottom: 1em;
}

.item-info-title {
  margin-bottom: 0.2em;
  font-family: 'Montserrat', sans-serif;
  font-size: calc(3em + 1vw);
  color: white;
}

.dramatic-entrance {
  animation-name: info_enterFromRight;
  animation-duration: 1s;
  animation-timing-function: ease;
  left: 60vw;
}

.dramatic-exit {
  animation-name: info_exitToRight;
  animation-duration: 1s;
  animation-timing-function: ease;
  left: 100vw;
}

@keyframes info_enterFromRight {
  0% {
    left: 100vw;
  }
  100% {
    left: 60vw;
  }
}

@keyframes info_exitToRight {
  0% {
    left: 60vw;
  }
  100% {
    left: 100vw;
  }
}
</style>
