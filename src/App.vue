<template>
  <div id="app">
    <worldPopAsync />
  </div>
</template>

<script>
import worldPopAsync from "./components/worldPopAsync.vue";
export default {
  name: "app",
  components: {
    worldPopAsync,
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
