<template>
  <div class="hello">
    <button v-on:click="createdPost()">MAJ</button>
    <ul>
      <li v-for="post in posts" :key="post">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  data() {
    return {
      posts: ["post1", "post2", "post3"],
    };
  },
  methods: {
    updatePost() {
      axios
        .get("https://jsonplaceholder.typicode.com/postsDD")
        .then((response) => (this.posts = response.data))
        .catch(
          (error) => (this.posts = [{ title: "erreur chargeemnt" + error }])
        );
    },
    createdPost() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", {
          id: 101,
          title: "foo",
          body: "bar",
          userId: 1,
        })
        .then((response) => console.log(response));
    },
  },
};
</script>

