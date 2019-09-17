<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo-restaurant.png">
    <RestaurantsList msg="Find your restaurants below"/>
  </div>
</template>
<script>
import RestaurantsList from "./components/RestaurantsList.vue";

export default {
  name: "app",
  components: {
    RestaurantsList
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
  padding-top: 60px;
  background: linear-gradient(
      rgba(255, 255, 255, 0.9),
      rgba(255, 255, 255, 0.8)
    ),
    url("./assets/background.jpg");
  background-size: contain;
}
</style>