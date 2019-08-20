<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      student: {
        firstName: "Peter",
        lastName: "Jang",
        email: "peter@email.com",
        phoneNumber: "123-456-7890",
        bio: "...",
        linkedinURL: "...@linkedin.com",
        twitterHandle: "@PJCoolIce",
        blog: "...@blog.com",
        resumeURL: "...@resume.com",
        gitHub: "...@gitHub.com",
        photo: "..."
      }
    };
  },
  created: function() {
    axios.get("https://jsonplaceholder.typicode.com/posts/1").then(response => {
      this.student = response.data;
    });
  },
  methods: {}
};
</script>
