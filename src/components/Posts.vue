<template>
  <div>
    <h2>Posts</h2>
    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.description }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["posts"],
  data() {
    return {
      // posts: MOCK_DATA,
    };
  },
};
</script>
