<template>
  <div class="PostsNew">
    <img v-if="status" :src="`https://http.cat/${status}`" />
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
        <!-- <small v-if="newPostsParams.body.length > 0 && newPostsParams.body.length < 150" class="text-danger">
          150 characters left
        </small>
        <small v-if="newPostsParams.password.length > 20" class="text-danger">
          Password cannot exceed 20 characters
        </small> -->
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
      status: "",
      newPostsParams: { body: "" },
    };
  },
  created: function () {
    axios.get(`/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.newPostsParams = response.data;
    });
  },
  methods: {
    updatePost: function () {
      console.log("Creating post!");
      // axios.patch(`/posts/${this.$route.params.id}`, this.currentPostsParams.then((response) => {
      //     console.log(response.data);
      //     this.$router.push(`/posts/${response.data.id}`);
      //   })
      axios
        .post("/posts", this.newPostParams)
        .then((response) => {
          this.$router.push("/posts");
          console.log(response.data);
        })
        .catch((error) => {
          this.status = error.response.status;
        });
    },
  },
};
</script>
