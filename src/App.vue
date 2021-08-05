<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <p>status</p>
    <p>{{ status }}</p>
  </div>
</template>

<script>
import HelloWorld from "./HelloWorld.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      status: 0,
    };
  },
  async mounted() {
    console.log(process.env.VUE_APP_API);
    const data = await axios.get(process.env.VUE_APP_API);
    console.log(data.status);
    this.status = data.status;
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
</style>
