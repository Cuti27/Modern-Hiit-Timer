<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="25%" />
    <hiit-timer></hiit-timer>
  </div>
</template>

<script>
import HiitTimer from "./components/HiitTimer";

export default {
  name: "App",
  components: {
    HiitTimer,
  },
};
</script>

<style lang="scss" scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
