<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  margin: 0;
  padding: 0;
  --parallax-bg-color: #fffee3;
  --description-bg-color: lightblue;
  --text-color: black;
}

a {
  text-decoration: none;
  color: black;
}
</style>
