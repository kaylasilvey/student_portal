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
                <li><a href="signin.html">Sign In</a></li>
                <li><a href="signup.html">Register</a></li>
              </ul>
              <!-- sign-in -->

              <a href="post.html" class="btn">Post Your Job</a>
            </div>
            <!-- nav-right -->
          </div>
          <!-- container -->
        </nav>
        <!-- navbar -->
      </header>
      <!-- header -->
      <div class="resume-content">
        <div class="profile section clearfix">
          <div class="profile-logo">
            <img class="img-fluid" src="images/job/resume.jpg" alt="Image" />
          </div>
          <div class="profile-info">
            <h1><!-- {{ student.firstName }} {{ student.lastName }} --></h1>
            <address>
              <p>
                Address: 123 West 12th Street, Suite 456 New York, NY 123456
                <br />
                Phone: +012 345 678 910
                <br />
                Email:
                <a href="#">
                  <span class="__cf_email__" data-cfemail="bad3cec9d7dffac9cfc8c0d3d6dfdddfdfd194d9d5d7">
                    [email&#160;protected]
                  </span>
                </a>
              </p>
            </address>
          </div>
        </div>
        <!-- profile -->
      </div>
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
