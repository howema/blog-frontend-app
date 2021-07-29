<template>
  <div id="app">
    <!-- <div id="nav">
      <li>
        <router-link to="/">Home</router-link>
      </li>
      |
      <li>
        <router-link to="/about">About</router-link>
      </li>
      |
      <li v-if="!isLoggedIn()">
        <router-link to="/signup">Signup</router-link>
        |
      </li>
      <li>
        <router-link to="/login">Login</router-link>
      </li>
      |
      <li v-if="!isLoggedIn()">
        <router-link to="/logout">Logout</router-link>
        |
      </li>
      <li>
        <router-link to="/posts">Posts</router-link>
      </li>
      |
      <li>
        <router-link to="/posts/new">Create</router-link>
      </li>
    </div> -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Cool Blog</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="/">
              Home
              <!-- <span class="sr-only">(current)</span> -->
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/signup">Signup</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/login">Login</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/posts">Posts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/posts/new">New</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/logout">Logout</a>
          </li>
          <!-- <li class="nav-item">
            <a class="nav-link" href="#">Pricing</a>
          </li>
          <li class="nav-item">
            <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a> -->
          <!-- </li> -->
        </ul>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  background-image: url("./assets/old_moon.png");
  text-align: center;
}
</style>

<script>
// import axios from "axios";
export default {
  methods: {
    isLoggedIn: function () {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
};
</script>
