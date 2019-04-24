<template>
  <div class="container">
    <button v-on:click="printresume()">Here is your resume</button>

    <h1>All Resumes</h1>
    <div v-for="resume in resumes">
      <h2>{{ resume.name }}</h2>
      <h2>{{ resume.title }}</h2>
      <h2>{{ resume.department }}</h2>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  data: function() {
    return {
      resumes: [
        {
          name: "Jordan",
          title: "Junior Buyer",
          department: "Retail"
        }
      ]
    };
  },
  created: function() {
    axios.get("/api/resumes").then(response => {
      this.resumes = response.data;
    });
  },
  methods: {
    printresume: function() {
      var pdf = new jsPDF();
      pdf.canvas.height = 72 * 11;
      pdf.canvas.width = 72 * 8.5;
      // pdf.setTextColor(0, 255, 0);

      pdf.fromHTML(document.querySelector("div.container"));
      pdf.save("test.pdf");
    }
  }
};
</script>
