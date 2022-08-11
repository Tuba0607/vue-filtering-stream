<template>
  <div>
    <h2>Filters</h2>
    <label for="search">
      Search
      <input id="search" v-model="term" @keypress.enter="search(term)" />
    </label>
    <p
      v-for="filter in filters"
      :key="filter.id"
      @click="() => filterPosts(filter)"
    >
      {{ filter }}
    </p>
  </div>
</template>
<script>
const filters = ["All", "HVAC", "Overhead Doors"];
export default {
  props: ["filterPosts", "search"],
  data() {
    return {
      filters,
      term: "",
    };
  },
};
</script>
