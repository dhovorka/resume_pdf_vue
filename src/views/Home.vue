<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App This is Sandy. Screw Dan." />
    <p>{{ message }}</p>

    <div>
      <button v-on:click="printresume()">Click to Print PDF</button>
    </div>
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
  methods: {
    printresume: function() {
      var pdf = new jsPDF();
      pdf.canvas.height = 72 * 11;
      pdf.canvas.width = 72 * 8.5;

      pdf.fromHTML(document.body);

      pdf.text("WE DID IT!", 10, 10);
      pdf.save("test.pdf");
    }
  }
};
</script>
