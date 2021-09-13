<template>
  <div id="app">
    <world-pop />
  </div>
</template>

<script>
import worldPop from "./components/worldPop.vue";
export default {
  name: "app",
  components: {
    worldPop,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
