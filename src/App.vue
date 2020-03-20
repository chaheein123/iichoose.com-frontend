<template>
  <v-app>
    <div id="app">
      <LandingPage />
    </div>
  </v-app>
</template>

<script>
import LandingPage from "./pages/LandingPage/LandingPage";

export default {
  name: "App",
  components: {
    LandingPage
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
