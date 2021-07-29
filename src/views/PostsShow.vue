<template>
  <div class="postsshow">
    <div class="container">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <li v-if="$parent.getUserId() == post.user_id">
        <router-link v-bind:to="`/posts/${post.id}/edit`"><button>Edit Post</button></router-link>
      </li>
      <!-- <img v-bind:src="post.image" alt="post.title" /> -->
      <p></p>
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
    axios.get("/posts/" + this.$route.params.id).then((response) => {
      this.post = response.data;
      console.log(response.data);
    });
  },
};
</script>
