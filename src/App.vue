<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <intro-content msg="Contacts" />
    <infinite-scroll />
  </div>
</template>

<script>
import IntroContent from "./components/IntroContent.vue";
import InfiniteScroll from "./components/InfiniteScroll.vue";

export default {
  name: "app",
  components: {
    IntroContent,
    InfiniteScroll
  }
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
