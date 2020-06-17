<template>
  <div id="app">
    <Home />
  </div>
</template>

<style>
html body #app {
  width: 100%;
  height: 100%;
}
</style>

<script>
import Home from "./components/Home.vue";

export default {
  name: "App",
  components: {
    Home
  }
};
</script>


