<template>
  <div v-if="dev">
    <h3>Dev Details</h3>
    <!-- <p>The dev id is {{ $route.params.id }}</p> -->
    <h3>{{ dev.title }}</h3>
    <p>dev id is {{ id }}</p>
    <p>{{ dev.details }}</p>
  </div>
  <div v-else>loading...</div>
</template>

<script>
// import devdata from "../../../data/db.json";
export default {
  props: ["id"],
  // don't need to define id in data when using props for parameter
  // but need to allow props: true in the route - index.js
  data() {
    return {
      // id: this.$route.params.id,
      dev: null,
      // devs: devdata,
    };
  },
  mounted() {
    fetch("http://localhost:3000/devs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.dev = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
</style>