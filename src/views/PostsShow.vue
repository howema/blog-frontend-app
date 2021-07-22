<template>
  <div class="postsshow">
    <div class="container">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <p>{{ post.image }}</p>
      <router-link to="/posts">Back to posts</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      errors: [],
      post: {},
    };
  },
  created: function () {
    axios.get("posts/10").then((response) => {
      this.post = response.data;
    });
  },
};
</script>
