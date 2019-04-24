<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App This is Sandy. Screw Dan." />
    <p>{{ message }}</p>


  </div>
</template>

<script>
// @ is an alias to /src
var axios = require("axios");
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  },
  data: function() {
    return {
      message: "Hello"
    };
  },
  methods: {}
};
</script>
