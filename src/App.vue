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

<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <intro-content msg="Contacts" />
    <contact-listing :take="10"/>
  </div>
</template>

<script>
import IntroContent from "./components/IntroContent.vue";
import ContactListing from "./components/ContactListing.vue";

export default {
  name: "app",
  components: {
    IntroContent,
    ContactListing
  }
};
</script>
