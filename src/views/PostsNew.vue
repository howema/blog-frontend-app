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
      newPostsParams: {},
    };
  },
  methods: {
    createPost: function () {
      console.log("Creating post!");
      axios.post("/posts", this.newPostsParams).then((response) => {
        this.$router.push("/posts");
        console.log(response.data);
      });
    },
  },
};
</script>
