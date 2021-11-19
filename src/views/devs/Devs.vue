<template>
  <h2>Devs</h2>
  <div v-if="devs.length">
    <div v-for="dev in devs" :key="dev.id" class="dev">
      <router-link :to="{ name: 'DevDetails', params: { id: dev.id } }">
        <h3>{{ dev.title }}</h3>
      </router-link>
    </div>
  </div>
  <div v-else>loading...</div>
</template>

<script>
export default {
  data() {
    return {
      // devs: [
      //   { title: "Web Developer", details: "lorem", id: 1 },
      //   { title: "Web Designer", details: "lorem", id: 2 },
      //   { title: "Vue Developer", details: "lorem", id: 3 },
      // ],
      devs: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/devs")
      .then((res) => res.json())
      .then((data) => (this.devs = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
</style>