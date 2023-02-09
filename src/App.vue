<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <!-- <FormBinding1></FormBinding1> -->
    <!-- <FormBinding2></FormBinding2> -->
    <!-- <FormBinding3></FormBinding3> -->
    <!-- <FormBinding4></FormBinding4> -->
    <!-- <ImgBinding></ImgBinding> -->
    <StyleBinding></StyleBinding>
  </div>
</template>

<script>
// import FormBinding1 from "@/views/FormBinding1.vue";
// import FormBinding2 from "./views/FormBinding2.vue";
// import FormBinding3 from "./views/FormBinding3.vue";
// import FormBinding4 from "./views/FormBinding4.vue";
// import ImgBinding from "./views/ImgBinding.vue";
import StyleBinding from "./views/StyleBinding.vue";
export default {
  name: "App",
  components: {
    // FormBinding1,
    // FormBinding2,
    // FormBinding3,
    // FormBinding4,
    // ImgBinding,
    StyleBinding,
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
dl {
  margin: 30px;
}
dt {
  font-weight: bold;
  margin-top: 50px;
}
</style>
