<template>
  <div class="PostsNew">
    <form v-on:submit.prevent="createPost()">
      <h1>New Post</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Title:</label>
        <input type="text" v-model="newPostsParams.title" />
      </div>
      <div>
        <label>Body:</label>
        <input type="text" v-model="newPostsParams.body" />
      </div>
      <div>
        <label>Image:</label>
        <input type="text" v-model="newPostsParams.image" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      errors: [],
      currentPostsParams: {},
    };
  },
  created: function () {
    axios.get(`/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.currentPostParams = response.data;
    });
  },
  methods: {
    updatePost: function () {
      console.log("Creating post!");
      axios.patch(`/posts/${this.$route.params.id}`, this.currentPostsParams.then((response) => {
          console.log(response.data);
          this.$router.push(`/posts/${response.data.id}`);
        })
      );
    },
  },
};
</script>
