<template>
  <div class="home">
    <div class="resume-content">
      <div class="profile section clearfix">
        <div class="profile-logo">
          <img class="img-fluid" src="images/job/resume.jpg" alt="Image" />
        </div>
        <div class="profile-info">
          <h1>{{ student.first_name }} {{ student.last_name }}</h1>
          <p>{{ student.email }}</p>
          <p>{{ student.phone_number }}</p>
          <p>{{ student.short_bio }}</p>
          <p>{{ student.linkedin_url }}</p>
          <p>{{ student.twitter_handle }}</p>
          <p>{{ student.personal_url }}</p>
          <p>{{ student.resume_url }}</p>
          <p>{{ student.github_url }}</p>
          <p>{{ student.photo_url }}</p>
        </div>
      </div>
      <!-- profile -->

      <div class="experience">
        <h1>Experience</h1>
        <div v-for="experience in student.experiences">
          <h2>{{ experience.company_name }}</h2>
          <h2>{{ experience.job_title }}</h2>
          <h2>{{ experience.start_date }} | {{ experience.end_date }}</h2>
          <h2>{{ experience.details }}</h2>
        </div>
        <div class="education">
          <h1>EDUCATION</h1>
          <div v-for="education in student.educations">
            <h2>{{ education.university_name }}</h2>
            <h2>{{ education.start_date }} | {{ education.end_date }}</h2>
            <h2>{{ education.degree }}</h2>
          </div>
        </div>

        <div class="capstone">
          <h1>CAPSTONE</h1>
          <div v-for="capstone in student.capstones">
            <h2>{{ capstone.name }}</h2>
            <h2>{{ capstone.description }}</h2>
            <h2>{{ capstone.url }}</h2>
            <h2>{{ capstone.screenshot_url }}</h2>
          </div>
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
        first_name: "",
        last_name: "",
        email: "",
        phone_number: "",
        bio: "",
        linkedin_url: "",
        twitter_handle: "",
        personal_url: "",
        resume_url: "",
        github_url: "",
        photo: "",
        experiences: [],
        education: [],
        capstone: []
      }
    };
  },
  created: function() {
    axios.get("https://sleepy-citadel-35395.herokuapp.com/api/students/1").then(response => {
      this.student = response.data;
    });
  },
  methods: {
    experienceEdit: function() {
      var params = {
        startDate: this.student.experiences.start_date,
        endDate: this.student.experiences.end_date,
        jobTitle: this.student.experiences.job_title,
        company: this.student.experiences.company,
        details: this.student.experiences.details
      };
      axios.patch(`/api/experiences/${this.student.experiences.id}`).then(response => {
        this.$router.push("/");
      });
    },

    educationEdit: function() {
      var params = {
        startDate: this.student.eductions.start_date,
        endDate: this.student.eductions.end_date,
        jobTitle: this.student.eductions.degree,
        company: this.student.eductions.university,
        details: this.student.eductions.details
      };
      axios.patch(`/api/eductions/${this.student.eductions.id}`).then(response => {
        this.$router.push("/");
      });
    },

    skillsEdit: function() {
      var params = {
        skill_name: this.student.skills.skill_name
      };
      axios.patch(`/api/skills/${this.student.skills.id}`).then(response => {
        this.$router.push("/");
      });
    },

    capstoneEdit: function() {
      var params = {
        name: this.student.capstones.name,
        description: this.student.capstones.description,
        url: this.student.capstones.url,
        screenshot: this.student.capstones.screenshot
      };
      axios.patch(`/api/capstones/${this.student.capstones.id}`).then(response => {
        this.$router.push("/");
      });
    }
  }
};
</script>
