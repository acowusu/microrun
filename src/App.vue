<template>
  <div id="app">
    <h1>Micro Marathon</h1>
    <h2>Laps: {{ laps }}</h2>
    <Timer message="Active Time" />
  </div>
</template>

<script>
import Timer from "./components/Timer";

export default {
  data() {
    return {
      laps: 0,
    };
  },
  name: "App",
  components: {
    Timer,
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
