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
        photo: "...",
        experience: [
          {
            startDate: "1/1/1901",
            endDate: "1/2/1902",
            jobTitle: "Headmaster",
            company: "Hogwarts",
            details: "... .... ..."
          },
          {
            startDate: "1/2/1902",
            endDate: "8/19/2019",
            jobTitle: "Headmaster",
            company: "Actualize",
            details: "... .... ..."
          }
        ],
        education: [
          {
            startDate: "9/1/1894",
            endDate: "1/1/1901",
            degree: "Muggle Studies",
            university: "Hogwarts",
            details: "... .... ..."
          }
        ],
        skills: ["Ruby", "HTML", "Potions", "Strong Earth Magnets", "Arithmancy"],
        capstone: {
          name: "Magical Applications of Computer Programming",
          description: "...",
          url: "capstone@hogwarts.edu",
          screenshot: "..."
        }
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
