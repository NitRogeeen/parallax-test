<template>
  <div id="app">
    <parallax-test/>
  </div>
</template>

<script>
import ParallaxTest from "./view/ParallaxTest";

export default {
  name: "App",
  components: {
    ParallaxTest
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Lato","Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
