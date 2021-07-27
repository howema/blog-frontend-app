<template>
  <div class="postsindex">
    <div class="card">
      <div
        v-for="post in posts"
        :key="post.id"
        v-bind:class="{ selected: post === currentPost }"
        v-on:click="currentPost = post"
      >
        <img class="card-img-top" v-bind:src="post.image" alt="Card image cap" />
        <div class="card-body">
          <h5 class="card-title">{{ post.title }}</h5>
          <p class="card-text">{{ post.body }}</p>
          <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
        </div>
      </div>
    </div>
<!-- 
    <h1>Here Come the Posts!</h1>
    <!-- <router-link to="/posts/10">Check out this gator</router-link> -->
    <!-- <div v-for="post in posts" :key="post.id">     ##links the image and text
      <router-link v-bind:to="`/posts/${post.id}`">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
        <img v-bind:src="post.image" alt="post.title" />
      </router-link> --> -->
      <!-- <p></p> -->
      <!-- <button>Buttonz!</button> -->
    </div>
  </div>
</template>

<style>
.card {
  width: 50%;
}
.selected {
  color: white;
  background-color: purple;
  transition: background-color 1s ease;
}
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Here are posts",
      posts: [],
      currentPost: {},
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
