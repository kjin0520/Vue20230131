<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <ClickEvent></ClickEvent> -->
    <!-- <InputEvent></InputEvent> -->
    <!-- <ChangeEvent></ChangeEvent> -->
    <KeyEvent></KeyEvent>
  </div>
</template>

<script>
// import ClickEvent from "@/views/ClickEvent.vue";
// import InputEvent from "@/views/InputEvent.vue";
// import ChangeEvent from "@/views/ChangeEvent.vue";
import KeyEvent from "@/views/KeyEvent.vue";

export default {
  name: "App",
  components: {
    // ClickEvent,
    // InputEvent,
    // ChangeEvent,
    KeyEvent,
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
  margin-top: 50px;
  margin-bottom: 20px;
}

h2 {
  margin-top: 50px;
}
</style>
