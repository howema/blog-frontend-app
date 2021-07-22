<template>
  <div class="postsindex">
    <h1>Here Come the Posts!</h1>
    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <img v-bind:src="post.image" alt="post.title" />
      <p></p>
      <button>Buttonz!</button>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Here are posts",
      posts: [],
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex: function () {
      axios.get("http://localhost:3000/posts").then((response) => {
        this.posts = response.data;
        console.log("All posts:", this.posts);
      });
    },
  },
};
</script>
