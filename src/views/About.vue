<template>
  <div class="container">
    <h1>All Resumes</h1>
    <div v-for="student in students">
      <p>First Name: {{ student.first_name }}</p>
      <p>Last Name: {{ student.last_name }}</p>
      <p>Email: {{ student.email }}</p>
      <p>Phone: {{ student.phone_number }}</p>
      <p>Bio: {{ student.short_bio }}</p>
      <p>Linkedin: {{ student.linkedin_url }}</p>
      <p>Twitter: {{ student.twiter_handle }}</p>
      <p>Website: {{ student.personal_website_url }}</p>
      <p>Github: {{ student.github_url }}</p>
      <p>Online: {{ student.online_resume_url }}</p>
      <p>Photo: {{ student.photo_url }}</p>
      <button v-on:click="printresume()">Here is your resume</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      students: []
    };
  },
  created: function() {
    axios.get("https://salty-gorge-38704.herokuapp.com/api/students/").then(response => {
      this.students = response.data;
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
