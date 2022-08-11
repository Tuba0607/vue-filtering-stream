<template>
  <div id="app" class="container">
    <div class="half">
      <Filters :filterPosts="filterPosts" :search="search" />
    </div>
    <div class="half">
      <Posts :posts="posts" />
    </div>
  </div>
</template>

<script>
import Posts from "./components/Posts.vue";
import Filters from "./components/Filters.vue";

import MOCK_DATA from "./MOCK_DATA.json";

export default {
  name: "App",
  components: {
    Posts,
    Filters,
  },
  data() {
    return {
      posts: MOCK_DATA,
      str: "",
      type: "",
    };
  },
  methods: {
    filterPosts(categoryName) {
      this.posts = MOCK_DATA;
      if (categoryName !== "All") {
        this.posts = this.posts.filter((post) => {
          return post.category === categoryName;
        });
      }
    },
    search(term) {
      this.resetPosts();
      this.posts = this.posts.filter((post) => {
        return post.title.toLowerCase().includes(term.toLowerCase());
      });
    },
    resetPosts() {
      this.posts = MOCK_DATA;
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  margin: 20px;
}
.half {
  width: 40%;
}
</style>
