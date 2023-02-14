<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <VIfVShowRendering1></VIfVShowRendering1> -->
    <!-- <VIfVShowRendering2></VIfVShowRendering2> -->
    <!-- <VIfVShowRendering3></VIfVShowRendering3> -->

    <!-- <ListRendering1></ListRendering1> -->
    <ListRendering2></ListRendering2>
  </div>
</template>

<script>
// import VIfVShowRendering1 from "@/views/VIfVShowRendering1.vue";
// import VIfVShowRendering2 from "@/views/VIfVShowRendering2.vue";
// import VIfVShowRendering3 from "@/views/VIfVShowRendering3.vue";

// import ListRendering1 from "@/views/ListRendering1.vue";
import ListRendering2 from "@/views/ListRendering2.vue";
export default {
  name: "App",
  components: {
    // VIfVShowRendering1,
    // VIfVShowRendering2,
    // VIfVShowRendering3,

    // ListRendering1,
    ListRendering2,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
dt {
  font-weight: bold;
  margin: 20px 0;
}
dd {
  margin-bottom: 10px;
}
</style>
