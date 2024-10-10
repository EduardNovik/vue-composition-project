<script>
export default {
  data() {
    return {
      name: "Vue tittle",
      status: "active",
      tasks: ["first", "second", "third"],
      link: "https://www.google.com/",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "pending";
      } else if (this.status === "pending") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
    },
  },
};
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is inactive</p>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <a :href="link" target="_blank">Go to google</a>
    <br />
    <!-- <button v-on:click="toggleStatus">Toggle</button> -->
    <button @click="toggleStatus">Toggle</button>
  </div>
</template>

<style scoped>
div {
  display: block;
}
</style>
