<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
<<<<<<< HEAD
    <HelloWorld msg="Welcome to Your Vue.js App This is Sandy. Screw Dan." />
    <p>{{ message }}</p>

    <div>
      <button v-on:click="printresume()">Click to Print PDF</button>
    </div>
=======
    <HelloWorld msg="Welcome to Your Vue.js App This is Sandy. Screw Dan. Killing it" />
>>>>>>> e4159eb11f19e5ea19fa501fe6d9582f1e69d95d
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
