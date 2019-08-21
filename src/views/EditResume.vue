<template>
  <div class="container edit">
    <form v-on:submit.prevent="experienceEdit()">
      <h2>Experience</h2>
      <div v-for="experience in student.experiences">
        <div>
          Company:
          <input type="text" v-model="experience.company_name" />
        </div>
        <div>
          Job Title:
          <input type="text" v-model="experience.job_title" />
        </div>
        <div>
          Start Date:
          <input type="text" v-model="experience.start_date" />
        </div>
        <div>
          End Date:
          <input type="text" v-model="experience.end_date" />
        </div>
        <div>
          Details:
          <input type="text" v-model="experience.details" />
        </div>
      </div>
    </form>

    <form v-on:submit.prevent="educationEdit()">
      <h2>Education</h2>
      <div v-for="education in student.educations">
        <div>
          University:
          <input type="text" v-model="education.university_name" />
        </div>
        <div>
          Degree:
          <input type="text" v-model="education.degree" />
        </div>
        <div>
          Start Date:
          <input type="text" v-model="education.start_date" />
        </div>
        <div>
          End Date:
          <input type="text" v-model="education.end_date" />
        </div>
        <div>
          Details:
          <input type="text" v-model="education.details" />
        </div>
      </div>
    </form>

    <form v-on:submit.prevent="skillEdit()">
      <h2>Skills</h2>
      <div v-for="skill in student.skills">
        <input type="text" v-model="skill.skill_name" />
      </div>
    </form>

    <form v-on:submit.prevent="capstoneEdit()">
      <h2>Capstone</h2>
      <div v-for="capstone in student.capstones">
        <div>
          Name:
          <input type="text" v-model="capstone.name" />
        </div>
        <div>
          Description:
          <input type="text" v-model="capstone.description" />
        </div>
        <div>
          URL:
          <input type="text" v-model="capstone.url" />
        </div>
        <div>
          Screenshot:
          <input type="text" v-model="capstone.screenshot" />
        </div>
      </div>
    </form>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      // student: {
      //   firstName: "Peter",
      //   lastName: "Jang",
      //   email: "peter@email.com",
      //   phoneNumber: "123-456-7890",
      //   bio: "...",
      //   linkedinURL: "...@linkedin.com",
      //   twitterHandle: "@PJCoolIce",
      //   blog: "...@blog.com",
      //   resumeURL: "...@resume.com",
      //   gitHub: "...@gitHub.com",
      //   photo: "...",
      //   experiences: [
      //     {
      //       startDate: "1/1/1901",
      //       endDate: "1/2/1902",
      //       jobTitle: "Headmaster",
      //       company: "Hogwarts",
      //       details: "... .... ..."
      //     },
      //     {
      //       startDate: "1/2/1902",
      //       endDate: "8/19/2019",
      //       jobTitle: "Headmaster",
      //       company: "Actualize",
      //       details: "... .... ..."
      //     }
      //   ],
      //   educations: [
      //     {
      //       startDate: "9/1/1894",
      //       endDate: "1/1/1901",
      //       degree: "Muggle Studies",
      //       university: "Hogwarts",
      //       details: "... .... ..."
      //     }
      //   ],
      //   skills: [
      //     {
      //       skill_name: "Ruby"
      //     },
      //     {
      //       skill_name: "HTML"
      //     },
      //     {
      //       skill_name: "Potions"
      //     },
      //     {
      //       skill_name: "Rare Earth Magnets"
      //     },
      //     {
      //       skill_name: "Arithmancy"
      //     }
      //   ],
      //   capstones: [
      //     {
      //       name: "Magical Applications of Computer Programming",
      //       description: "...",
      //       url: "capstone@hogwarts.edu",
      //       screenshot: "..."
      //     }
      //   ]
      // }
      student: {}
    };
  },
  created: function() {
    axios.get("https://sleepy-citadel-35395.herokuapp.com/api/students").then(response => {
      this.student = response.data;
    });
  },
  methods: {
    experienceEdit: function() {
      var params = {
        startDate: this.student.experience.start_date,
        endDate: this.student.experience.end_date,
        jobTitle: this.student.experience.job_title,
        company: this.student.experience.company,
        details: this.student.experience.details
      };
      axios.patch(`/api/experiences/${this.student.experience.id}`).then(response => {
        this.$router.push("/");
      });
    },

    educationEdit: function() {
      var params = {
        startDate: this.student.education.start_date,
        endDate: this.student.education.end_date,
        jobTitle: this.student.education.degree,
        company: this.student.education.university,
        details: this.student.education.details
      };
      axios.patch(`/api/educations/${this.student.education.id}`).then(response => {
        this.$router.push("/");
      });
    },

    skillsEdit: function() {
      var params = {
        skill_name: this.student.skill.skillname
      };
      axios.patch(`/api/skills/${this.student.skill.id}`).then(response => {
        this.$router.push("/");
      });
    },

    capstoneEdit: function() {
      var params = {
        name: this.student.capstone.name,
        description: this.student.capstone.description,
        url: this.student.capstone.url,
        screenshot: this.student.capstone.screenshot
      };
      axios.patch(`/api/capstones/${this.student.capstone.id}`).then(response => {
        this.$router.push("/");
      });
    }
  }
};
</script>
