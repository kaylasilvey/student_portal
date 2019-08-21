<template>
  <div id="app">
    <body>
      <!-- header -->
      <header id="header" class="clearfix">
        <!-- navbar -->
        <nav class="navbar navbar-default navbar-expand-lg">
          <div class="container">
            <button
              class="navbar-toggler"
              type="button"
              data-toggle="collapse"
              data-target="#navbarNav"
              aria-controls="navbarNav"
              aria-expanded="false"
              aria-label="Toggle navigation"
            >
              <span class="navbar-toggler-icon"><i class="fa fa-align-justify"></i></span>
            </button>
            <a class="navbar-brand" href="index.html">
              <img class="img-fluid" src="images/logo.png" width="40" alt="Logo" />
            </a>

            <div class="collapse navbar-collapse" id="navbarNav">
              <ul class="nav navbar-nav">
                <li><a href="index.html">Home</a></li>
                <li><a href="resume.html">Resume</a></li>
              </ul>
            </div>

            <!-- nav-right -->
            <div class="nav-right">
              <ul class="sign-in">
                <li><i class="fa fa-user"></i></li>
                <li><a href="/login">Sign In</a></li>
              </ul>
              <!-- sign-in -->
            </div>
            <!-- nav-right -->
          </div>
          <!-- container -->
        </nav>
        <!-- navbar -->
      </header>
      <!-- header -->

      <router-view />
    </body>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data: function() {
    return {};
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
