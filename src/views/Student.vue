<template>
  <div class="home">
    <h1>{{ student.firstName }} {{ student.lastName }}</h1>
    <h2>{{ student.email }}</h2>
    <h2>{{ student.phoneNumber }}</h2>
    <h2>{{ student.bio }}</h2>
    <h2>{{ student.linkedinURL }}</h2>
    <h2>{{ student.twitterHandle }}</h2>
    <h2>{{ student.blog }}</h2>
    <h2>{{ student.resumeURL }}</h2>
    <h2>{{ student.gitHub }}</h2>
    <h2>{{ student.photo }}</h2>
    <div class="experience">
      <h1>Experience</h1>
      <div v-for="experience in student.experience">
        <h2>{{ experience.company }}</h2>
        <h2>{{ experience.jobTitle }}</h2>
        <h2>{{ experience.startDate }} | {{ experience.endDate }}</h2>
        <h2>{{ experience.details }}</h2>
      </div>
      <div class="education">
        <h1>EDUCATION</h1>
        <div v-for="education in student.education">
          <h2>{{ education.university }}</h2>
          <h2>{{ education.degree }}</h2>
          <h2>{{ education.startDate }} | {{ education.endDate }}</h2>
          <h2>{{ education.details }}</h2>
        </div>
      </div>
      <div class="skillz">
        <h1>SKILLS</h1>
        <div v-for="skill in student.skills">
          <h2>{{ skill }}</h2>
        </div>
      </div>
      <div class="capstone">
        <h1>CAPSTONE</h1>
        <div v-for="capstone in student.capstone">
          <h2>{{ capstone.name }}</h2>
          <h2>{{ capstone.description }}</h2>
          <h2>{{ capstone.url }}</h2>
          <h2>{{ capstone.screenshot }}</h2>
        </div>
      </div>
    </div>
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
        skills: ["Ruby", "HTML", "Potions", "Rare Earth Magnets", "Arithmancy"],
        capstone: [
          {
            name: "Magical Applications of Computer Programming",
            description: "...",
            url: "capstone@hogwarts.edu",
            screenshot: "..."
          }
        ]
      }
    };
  },
  created: function() {
    axios.get("https://sleepy-citadel-35395.herokuapp.com/api/students").then(response => {
      this.student = response.data;
      console.log("info", this.student);
    });
  },
  methods: {}
};
</script>
